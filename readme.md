## Description
This is a logging handler for Python's [logging](https://docs.python.org/3/library/logging.html) module to send log messages over [sendinblue](https://www.sendinblue.com/)'s transactional email service.

## Installation
```shell
cd $(python -m site --user-site)
gh repo clone calwarhurst/sendinblue-logger
```

## Usage
```python
from sendinblue import sendinblue
import logging
import os

handler = sendinblue.LoggingHandler(
    level=logging.ERROR,
    api_key=os.environ['SENDINBLUE_API_KEY'],
    from_email='sender-email@domain.com',
    to_email='recipient-email@domain.com',
)

logging_config = {
    'filename': '/home/user/project/project.log', 
    'encoding': 'utf-8', 
    'level': logging.DEBUG, 
    'format': '%(asctime)s - %(levelname)s: %(message)s',
    'handlers': (handler,),
}

logging.basicConfig(**logging_config)
```
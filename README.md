[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)  [![PyPi Python Versions](https://img.shields.io/pypi/pyversions/yt2mp3.svg)](https://pypi.python.org/pypi/yt2mp3/)

# Amazon Captcha Solver
A Flask API based solution for tackling captcha when collecting data from Amazon.

This is a Flask API based solution to solve the captcha, by accepting the captcha image from POST request. The API then calls the captcha solving script and sends the solved captcha text in return.

The goal is to solve the captcha images from Amazon. Sample captcha image can be seen below -

![a sample captcha image](https://github.com/HRN-Projects/captcha-solver/blob/main/test_captchas/Captcha_iwhygarbwz.jpg)
<br>

## How to use : ##
1. Run the Flask API script -
```
python solve_api.py
```

2. To check the status of API, call the default method by accessing its IP -
```
your_api_ip_address:5000    # '5000' being the default port for Flask Server, which hosts the API.
```

3. To call the captcha solver function with 'requests' module and passing captcha image as file -
```
import requests

def captcha_uploader():
    # API URL with a call to function to solve captcha
    captcha_solver_api_url = 'your_api_ip_address:5000/solve'
    # opening the captcha image file as binary and putting it as value for key 'captcha'
    file = {'captcha': open('your_captcha_image_filepath','rb')}
    
    # Calling the API function as a 'POST' request with 'files' parameter
    response = requests.post(captcha_solver_api_url, files=file)
    print("Captcha file uploaded.")

    # Fetching the captcha text from API response.
    try:
        captcha_text = resp.json()['output']
    except:
        print("Response not in JSON format. Please check your API code.")
        captcha_text = "NA"
    
    return captcha_text
```
<br>

## How to contribute : ##
1. Please start with installing all the required packages from requirements file-
  ```
  pip install -r requirements.txt
  ```

2. Then to initially run the model on test_captchas, use following command -
  ```
  python solve_captchas_with_model.py
  ```
<br>

## P.S. Notes : ##
### Regarding model file ###
The current model file is built after training some 4K training set captcha images.
Training can performed on much more larger dataset for better results, but current results aren't bad either :wink:.


### Regarding API code ###
The API works fine but can be enhanced further according to use cases. The API's reponses would highly depend upon the training quality of the model file.


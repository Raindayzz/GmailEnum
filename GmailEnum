import requests
import json
import argparse



parser = argparse.ArgumentParser()
parser.add_argument("-f", dest="inputFile", required=True)
parser.add_argument("-d", dest="domain", required=True)
parser.add_argument("-o", dest="output", required=True)
args = parser.parse_args()

def prRed(skk): print("\033[91m {}\033[00m" .format(skk))
def prGreen(skk): print("\033[92m {}\033[00m" .format(skk))
def prLightPurple(skk): print("\033[94m {}\033[00m" .format(skk))
def prPurple(skk): print("\033[95m {}\033[00m" .format(skk))

print(r"""\  ________               .__.__  ___________                     
 /  _____/  _____ _____  |__|  | \_   _____/ ____  __ __  _____  
/   \  ___ /     \\__  \ |  |  |  |    __)_ /    \|  |  \/     \ 
\    \_\  \  Y Y  \/ __ \|  |  |__|        \   |  \  |  /  Y Y  \
 \______  /__|_|  (____  /__|____/_______  /___|  /____/|__|_|  /
        \/      \/     \/                \/     \/            \/ """)

inputter = open(args.inputFile, "r")
test = open(args.inputFile, "r")
test1 = open(args.inputFile, "r")
URL = "https://mail.google.com/mail/gxlu?email="
x = (len(test.readlines()))
prPurple("Total accounts to be enumerated: " + str(x))
prPurple("--------------------------------")
ticker=0
normalized=0
for user in test1:
    if user.find("@") != -1:
        normalized=normalized+1
    if ticker == 10: break
    ticker=ticker+1
validAccounts = []

for user in inputter:
    if normalized == 0:
        email = user.strip() + "@" + args.domain
    elif normalized == 11:
        email = user.strip()
    else:
        print ("Something is not quite right, make sure you input file is either all email addresses or usernames")

    URLReq = "https://mail.google.com/mail/gxlu?email=" + email
    r = requests.get(url=URLReq)
    data = str(r.headers)
    index = data.find("Set-Cookie")
    if data.find("Set-Cookie") != -1:
        prGreen("[+] " + email + " is a valid account")
        validAccounts.append(email)
    else:
        prRed("[-] " + email + " not valid")


if args.output != "":
    with open(args.output, 'w') as fp:
        for item in validAccounts:
            fp.write("%s\n" % item)
    prPurple("--------------------------------")
    prPurple(str(len(validAccounts)) + " valid accounts out of " + str(x))
    prPurple("Valid Accounts saved to: " + args.output)
    

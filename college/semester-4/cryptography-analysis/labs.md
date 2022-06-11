# Lab 1: Firefox: Logins and passwords

For more details please consult the [Firefox: Logins and Passwords](https://attackdefense.com/challengedetails?cid=166) challenge.

> n this forensics exercise,  Firefox is installed on the system and all required tools are present on the system. The exercise is supposed to be done manually using first principles of analyzing Firefox preference data. 

> You have to find the answers to the following questions:

## Logins and Passwords

- What is the encrypted username for aliexpress.com ?

```bash
# List all hidden files and folders
ls -lar
cd .mozilla/firefox/zevp8nk2.default/
cat logins.json | python -m json.tool
# Find the token which has the website aliexpress.com as a part of it
```

**Response**: MDIEEPgAAAAAAAAAAAAAAAAAAAEwFAYIKoZIhvcNAwcECIBTJSVn65xZBAgEPe0Xx07MEg==

- User has changes his password for one of the websites. Which website is that?

```bash
cat logins.json | python -m json.tool
# Manually check the output to see when "timeCreated" and "timePasswordChanged" do not match
```

**Response**: https://github.com

- After how many hours the password was changed (in continuation to the above question)?

```bash
cat logins.json | python -m json.tool
# Calculate the difference between "timeCreated" and "timePasswordChanged", then divide it by 1000 to get seconds
# Further divide the output by 3600 to get hours
```

- When was the saved facebook password used by the user to login most recently (Answer in DD-MM-YY HH:MM:SS GMT)?

```bash
cat logins.json | python -m json.tool
# Get the value for "timeLastUsed", then convert it to seconds and pass it to the next command
​date -d @1539733955
```

- What is the master password used in Firefox?

To get this information run the following commands:

```bash
cd ../
vi profiles.ini
# Delete the last entry in the file
cd ~tools/firefox_decrypt/
ls -la
vi brute.sh
#! /bin/bash
input=$1
while IFS= read -r var
do
echo "Trying :$var"
echo "$var" | python firefox_decrypt.py
done < "$input"
# Save the file
chmod +x brute.sh
./brute.sh 1000000-password-seclists.txt
# Hit ^C as soon as you see the program find and answer
```

**Response**: qwer1234

- The first entry in the password list, is for which account?

Analyze the previous output to see which account is the first entry in the list.

**Response**: Firefox

- What email ID is used by the user on Github?

Analyze the previous output for the email ID.

**Response**: strange_people86@kmail.xyz

- What is the Facebook account password of the target user?

Analyze the previous output for the password.

**Response**: test@password@1234#

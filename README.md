# Keylogger

Keylogger is a a simple, yet effective, Keylogger that uses minimal resources and dependencies. It tracks all keyboard input, writes input to a log file, sends the file to an email address, then encrypts the local file. It can be customized to reflect any keymap with ease and depending on the use can be refactored to be more obscure.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

Supported Operating Systems: Windows 10, Windows 8, Windows 7

Supported Email Client: Gmail

To use the email feature, you must go into your Google Account settings for the "Sender" address, and allow less secure apps to sign in to the account. I reccommend creating a separate email account for this purpose.

For example:

A Windows 10 machine can run the keylogger and send the email using valid Gmail addresses. In the program, the "Sender" variables will contain the email and password to send the log files using a powershell script.

### Installing

1. Install CodeBlocks MinGW (codeblocks-17.12mingw-setup.exe) is the version I used.
2. Add -mwindows to compiler and linker options
3. Add support for C++11
4. Clone the repo
5. Make any adjustments to the program desired such as time intervals, email credentials, keymappings, etc.
6. Compile and build
7. Run the exe.

You will find the encrypted keylogs in: C:\Users\*Username\AppData\Roaming\Microsoft\CLR. 

If you would like to decrypt them, simply write the reverse of the encryption used as another console app and pass the log file as input and a new decrypted file as output. I may write one and upload it, but you get the readable keylogs sent over SMTP to your destination email already.

# Inspiration

I wanted to make something that would be doable in a day as a solo developer for the MLH Local Hack Day hackathon, as well as provide practical use in an ethical hacking, cybersecurity, and system administration setting.

## What it does

Keylogger runs silently in the background without permissions, gathers all key events, logs them into a file, sends that file securely over SMTP to the threat agents email, then encrypts the keylog on the infected host using a salted base64 encoding algorithm.

## How I built it

I built the project using Code::Blocks. The design pattern is OOP and is divided up into multiple functionalities via header files, then built the various functions required such as encryption, asynchronous time management, key hooks, the key map, email, as well as various helper functions.

## Challenges I ran into

Learning about asynchronous operations and object states was a difficult path to making everything not only run continuously in the background, but without being hindered by other operations. The powershell scripting for the email functionality was particularly cumbersome due to the conversion into a C++ string.

## Accomplishments that I'm proud of

I was pretty tempted to give up at making it work in the last 6 hours after finishing it. I had all of the code done, but couldn't debug it for hours to the point where I was about to just move on, but I stuck with the challenge and completed a working application that does everything I set out for it to do.

## What I learned

Powershell is not fun to manage through C++, and keyloggers can be pretty creepy.

## What's next for Keylogger

Next I will be building a front end to interact with the keylogger and display the outputs being sent from the infected test hosts. The idea is to allow anybody to see the logs online as a way to conceptualize the vulnerability. I'll probably have to add an SFTP script in the keylogger to send logs to a database to be displayed on the front end.

## Built With

* c++
* powershell

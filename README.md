# TencentComicBook

Tencent comics, Bilibili Comics, Demon comic reptile

## Features of this project

-[x] Comic Batch Download
-[x] Save sub-categories by chapter
-[x] Support Tencent Comic, Bilibili Comic, Youqi Comic
-[x] Support login
-[x] support generating pdf
-[x] Support sending to email
-[x] Integrate api to facilitate calling [API-README] (API-README.md)


## Installation dependencies

If you just download the picture, just install `requests` and eat it

`python3 -m pip install requests`

To generate pdf and send to mailbox, you need to install full dependencies

`python3 -m pip install -r requirements.txt`

** Note **: Information needs to be configured before sending to the mailbox

Copy `config.ini.example` and name it` config.ini`, and modify the parameters of `config.ini` according to the actual situation

## General use

Download by default from Tencent comics, pay attention to the comicid difference between different sites

-Download the latest episode of One Piece: `python3 -m onepiece`
-Download comic id = 505430 latest episode: `python3 -m onepiece --comicid = 505430`
-Download comics id = 505430 All chapters: `python3 -m onepiece --comicid = 505430 --all`
-Download comic id = 505430 Episode 800: `python3 -m onepiece --comicid = 505430 --chapter = 800`
-Download manga id = 505430 penultimate episode: `python3 -m onepiece --comicid = 505430 --chapter = -2`
-Download comics id = 505430 episodes 1 to 5, episode 7, 9 to 10: `python3 -m onepiece --comicid = 505430 --chapter = 1-5,7,9-10`
-Download comic id = 505430 and generate pdf file: `python3 -m onepiece --comicid = 505430 --pdf`
-Download the comic id = 505430 and push it to the mailbox: `python3 -m onepiece --comicid = 505430 --pdf --mail`
-Download from the mouse drawing comic: `python3 -m onepiece --site = ishuhui --comicid = 1 --chapter = 1-5`
-Download from Bilibili Manga: `python3 -m onepiece --site = bilibili --comicid = mc24742 --chapter = 1-5`
-Download from Enchanting Comics: `python3 -m onepiece --site = u17 --comicid = 195 --chapter = -1`

If you do n’t know or do n’t remember the comicid, you can search by name and enter the comicid as prompted

-`python3 -m onepiece --site = qq --name = Pirate --chapter = 1-5`
-`python3 -m onepiece --site = bilibili --name = Pirate --chapter = -1`
-`python3 -m onepiece --site = u17 --name = hinny bee --chapter = -1`


## Using help

`` `sh
# View help
python3 -m onepiece --help
`` `

`` `sh
usage: onepiece [-h] [-id COMICID] [--name NAME] [-c CHAPTER]
                [--worker WORKER] [--all] [--pdf] [--login] [--mail]
                [--config CONFIG] [-o OUTPUT] [--site {qq, u17, bilibili}]
                [--cachedir CACHEDIR] [--nocache] [--driver-path DRIVER_PATH]
                [--driver-type {Firefox, Ie, Opera, Chrome}]
                [--session-path SESSION_PATH] [-V] [--debug]

optional arguments:
  -h, --help show this help message and exit
  -id COMICID, --comicid COMICID
                        Comic id, One Piece: 505430
                        (http://ac.qq.com/Comic/ComicInfo/id/505430)
  --name NAME
  -c CHAPTER, --chapter CHAPTER
                        To download the chapter, the latest chapter is downloaded by default. E.g. -c 666 or -c 1-5,7,9-10
  --worker WORKER Number of thread pools. 4 thread pools are enabled by default.
  --all whether to download all chapters of the comic, such as --all
  --pdf whether to generate pdf files, such as --pdf
  --login Whether to log in to the account, such as --login
  --mail Whether to send pdf files to the mailbox, such as --mail. You need to configure email information in advance.
                        You can refer to the config.ini.example file to create and modify the config.ini file
  --config CONFIG configuration file path, default is config.ini in current directory
  -o OUTPUT, --output OUTPUT
                        File save path, default to the download folder under the current path
  --site {qq, u17, bilibili}
                        Data source website: support bilibili, qq, u17
  --cachedir CACHEDIR The image cache directory. The default is the current directory.
  --nocache disable image caching
  --driver-path DRIVER_PATH
                        selenium driver
  --driver-type {Firefox, Ie, Opera, Chrome}
                        Supported browsers: Chrome, Firefox, Ie, Opera. The default is Chrome
  --session-path SESSION_PATH
                        Read or save the last used session path
  -V, --version show program's version number and exit
  --debug debug
`` `

#### About login

Due to my limited ability, I ’m too lazy to log in, so I have to sacrifice the selenium killer.

1. Install selenium: `python3 -m pip install selenium`
2. Install chrome browser
3. [Download chromedriver] (https://chromedriver.chromium.org/downloads)
4. Log in and save cookies locally (save login status, save next time)
`` `sh
python3 -m onepiece --site = qq --comicid = 505430 --chapter = -1 \
  --login \
  --driver-path = "chromedriver-path" \
  --driver-type = "Chrome" \
  --session-path = ". cache / session.pickle"
`` `


**Disclaimer** : This project is for learning and communication purposes only. Do not use it for illegal purposes.

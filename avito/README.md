# Overview

Tested on Python 3.8.1 [MSC v.1916 32 bit (Intel)] on win32.

I suggest to use VPN (i use ProtonVPN) if your IP has been blocked, that would be much faster than proxies in proxies.txt.

## webbot py

webbot.py is a source code clone from [here](https://github.com/nateshmbhat/webbot). Thanks to this guy.
File was modified to define another `driverpath` for your webdriver to overcome some issues with pyinstaller, also selenium console log  made less verbose.

## avito_scraper.py

This is the main file which should be launched.

## core py

Core scraper functions. If initial page is paginated bot will crawl to the last page and collect links for each item. Links will be saved in file named 'urls_http-url-from-user-input.csv'. If bot was interrupted, then on the next time it will go through these saved urls in order not to load everything once again. Hence if url list is not complete you may want to delete everything in this file to download everything once more. Data from items will be saved in 'data_http-url-from-user-input.csv'. Data is saved on each iteration, so if bot was interrupted while collecting data from items, next time it will skip existing urls in 'data_http-url-from-user-input.csv'.

Also this app has a lazy protection, in order if you hand exe file to someone you don't fully trust. App will try to connect to the internet and if it can it will go to website specified in `core.py > check_app_status` function to look for permission. So you may want to disable it for personal use.

## utils py

Functions for reading, writing, formatting etc.

## settings py

Here you may want to specify `WEBDRIVERPATH` (in my case chrome_windows.exe) if you want to make executable. Or use just requests by changing `USE_BOT=False`. Changing `SLEEP_TIME` and `TIMEOUT` may affect the performance. Define selectors for the data you want to fetch from each item.

## proxies txt

Using these should work but will likely make bot crawl like a snail. Use `TIMEOUT` in settings.py to move faster to next proxy. Also change `SLEEP_TIME` if server blocks IPs too fast.

## bad_proxies txt

All used proxies are cloned here.

## errors txt

A place for errors that reach max tries.

## chrome_windows exe

You won't find it here, but you can find it on your system after installing selenium. However you can avoid using it by changing `USE_BOT=False` in setting.py. Looks like selenium is blocked less frequent by servers than requests in this setup.

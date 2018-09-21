In this exercise we will use the [Tornado Python web framework](http://www.tornadoweb.org/en/stable/) to create some simple web APIs that read and process information from a JSON file.


# Installation Instructions

Install the tornado python module using pip following a command such as,

$ sudo pip install tornado

This program runs the Tornado web framework in the port 8888. 


# Sample Application

The sample application distros.py reads a json file named distros.json. It reads through the json and lets you find the information of the instances of a particular operating system.

You may run the program using command line,

$ python distros.py

Now go to http://localhost:8888/?oid=[OPERATING_SYSTEM_NAME] using your browser.

For example 
http://localhost:8888/?oid=Ubuntu
or
http://localhost:8888/?oid=Debian

Alternatively, use curl:

$ curl http://localhost:8888/?oid=Debian
{"0": {"Name": "Debian", "ExecTime": "9", "Install": "apt", "Owner": "SPI", "Kernel": "4.9"}, "1": {"Name": "Debian", "ExecTime": "10", "Install": "apt", "Owner": "SPI", "Kernel": "4.9"}, "2": {"Name": "Debian", "ExecTime": "19", "Install": "apt", "Owner": "SPI", "Kernel": "4.9"}, "3": {"Name": "Debian", "ExecTime": "20", "Install": "apt", "Owner": "SPI", "Kernel": "4.9"}, "4": {"Name": "Debian", "ExecTime": "39", "Install": "apt", "Owner": "SPI", "Kernel": "4.9"}, "5": {"Name": "Debian", "ExecTime": "410", "Install": "apt", "Owner": "SPI", "Kernel": "4.9"}, "6": {"Name": "Debian", "ExecTime": "59", "Install": "apt", "Owner": "SPI", "Kernel": "4.9"}, "7": {"Name": "Debian", "ExecTime": "20", "Install": "apt", "Owner": "SPI", "Kernel": "4.9"}}


# Exercise

Adopt the given sample application to return the average execution time of any given operating system.

Expected outcome:
$ curl http://localhost:8888/?oid=Debian
{"distribution_id": "Debian", "avg_exec_time": 73.25}

# Hints
Here are two libraries that will help you make API calls in python

http://unirest.io

http://docs.python-requests.org/en/master/

# Port-Scanner
Customized Port Scanner for easy and efficient use, saving time by first analyzing open ports then deep scanning them.
The code in python is as follows:

#!/bin/python

import sys
import socket
from datetime import datetime

#Define our Target
if len(sys.argv) = 2:
      target = socket.gethostbyname(sys.argv[1])   #Translate hostanme to IPV4
else:
      print("Invalid amount of arguments")
      print("Syntax: python3 scanner.py <ip>")

#Adding a Banner
print("-" * 50)
print("Scanning target "+target)
print("Time started: "+str(datetime.now()))
print("-" * 50)

try:
        for port in range(50,85):
              s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
              socket.setdefaulttimeout(1)
              result = s.connect_ex((target,port))   #resturns an error indication
              if result = 0:
                    print("Port {} is open".format(port))
              s.close()
              
except KeyboardInterrupt:
        print("\nExiting program")
        sys.exit()
        
except socket.gaierror:
        print("Hostname could not be resolved")
        sys.exit()
        
except socket.error:
        print("Couldn't connect to server.")
        sys.exit()

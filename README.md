# EX01 Developing a Simple Webserver

# Date:7\10\2024
# AIM:
To develop a simple webserver to serve html pages and display the configuration details of laptop.

# DESIGN STEPS:
## Step 1:
HTML content creation.

## Step 2:
Design of webserver workflow.

## Step 3:
Implementation using Python code.

## Step 4:
Serving the HTML pages.

## Step 5:
Testing the webserver.

# PROGRAM:

```

views.py
from importlib.resources import contents
from django.shortcuts import render
from django.http import HttpResponse

contents='''<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lenovo ThinkPad E16 Gen 1 Specifications</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 20px;
            background-color: #0db7f0; 
            color: #333;
        }
        .container {
            max-width: 800px;
            margin: auto;
            padding: 20px;
            background: #472e83; 
            border: 1px solid #ddd;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h1 {
            text-align: center;
            color: #333;
        }
        ul {
            list-style: none;
            padding: 0;
        }
        ul li {
            background: #f9f9f9;
            margin: 10px 0;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        ul li:hover {
            background: #07cbf2; 
        }
        .footer {
            text-align: center;
            margin-top: 20px;
            font-size: 0.9em;
            color: #1a0202;
        }
        a {
            text-decoration: none;
            color: #0073e6;
        }
        a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Lenovo ThinkPad E16 Gen 1</h1>
        <h2>Specifications</h2>
        <ul>
            <li><strong>Processor:</strong> 13th Gen Intel(R) Core(TM) i5-1335U </li>
            <li><strong>Memory:</strong> 16GB LPDDR5 RAM</li>
            <li><strong>Display:</strong> 16-inch Full HD (1920 x 1200), 16:10 aspect ratio</li>
            <li><strong>Graphics:</strong> NIVIDIA GeForce GTX 1650</li>
            <li><strong>Storage:</strong> Up to 1TB PCIe NVMe SSD</li>
            <li><strong>Build:</strong> Lightweight aluminum chassis, ~1.8kg</li>
            <li><strong>Battery:</strong> 57Wh with rapid charging</li>
            <li><strong>Ports:</strong> USB-C, HDMI, and other options</li>
            <li><strong>Operating System:</strong> Windows 11</li>
        </ul>
        <div class="footer">
            <p>For more details, visit <a href="https://pcsupport.lenovo.com">Lenovo Support</a>.</p>
        </div>
    </div>
</body>
</html>
'''

def app(request):
    return HttpResponse("Hello India")
from http.server import HTTPServer,BaseHTTPRequestHandler
class MyServer(BaseHTTPRequestHandler):
    def do_GET(self):
        print("Get request received...")
        self.send_response(200)
        self.send_header("content-type","text/html")
        self.end_headers()
        self.wfile.write(contents.encode())
print("This is my webserver")
server_address =('',8000)
httpd = HTTPServer(server_address,MyServer)
httpd.serve_forever()


urls.py

from tempfile import template
from django.contrib import admin
from django.urls import path
from app.views import MyServer

urlpatterns = [
    path('admin/', admin.site.urls),
    path('server/',MyServer.as_view())
]
```

# OUTPUT:
![Screenshot 2024-12-06 223347](https://github.com/user-attachments/assets/b133f310-c442-454a-87a4-70fbe7274411)

![image](https://github.com/user-attachments/assets/a4f35b02-c6b3-4f82-aa04-dcdfa1a8d894)


# RESULT:
The program for implementing simple webserver is executed successfully.

# ServiceBusDemo
Demo App Services End‑to‑End with Azure Functions and Service Bus (Python)

📦 **Service Bus Sender App (SERVICEBUSQUEUELOAD)**
This folder contains two Python scripts that demonstrate how to send messages to an Azure Service Bus queue.
It’s meant to be run locally to load test data into the queue that the Function Apps will process.

📂 Files
File	Purpose
send_message.py	Simple synchronous sender using the azure-servicebus library.
load_queue.py	Asynchronous sender using asyncio and passwordless identity (or connection string).
requirements.txt	Python dependencies.
local.settings.json	Local environment configuration (optional).

🔧 Prerequisites
Install dependencies: pip install -r requirements.txt

In both examples, set your queue name and connection string (or use passwordless authentication):
CONNECTION_STR
QUEUE_NAME

✅ **1. send_message.py – Synchronous Example**

Libraries: azure-servicebus

Highlights:
-> Creates a ServiceBusClient using a connection string.
-> Creates a sender for the specified queue.
-> Iterates through a list of messages (Order #1001, Order #1002, etc.) and sends them synchronously.
-> Prints confirmation for each message sent.

👉 Use case:
Great for quick tests or small batch sends.

✅ **2. load_queue.py – Asynchronous Example**

Libraries:
azure-servicebus (async support)
asyncio

Highlights:
-> Uses async/await for high‑throughput sending.
-> Can run with passwordless authentication (Managed Identity) or connection strings, as shown in Microsoft docs( https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-python-how-to-use-queues?tabs=passwordless ).
-> Scales better when you need to send a large number of messages quickly.

🛠 Running the Sender App
Synchronous example: python send_message.py
Asynchronous example: python load_queue.py

✅ Both scripts will print ✅ Sent message: … and you should see messages arriving in your Service Bus queue.

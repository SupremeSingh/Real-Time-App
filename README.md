# Real-Time-App
A real time application using Alchemy Notify

For our architecture, we’ll use Express for our server, WebSockets to communicate between the client and server, and Alchemy Notify to monitor an address and send a push notification when there is activity on that address.

Our example dApp will perform two functions: First, it will register a user’s address for notifications, and second it will send a notification to that user when they receive or send transactions.

The “register a user’s address for notifications” flow looks like this:

- A user connects to their wallet through the dApp
- The user clicks to register their wallet address to be monitored
- The dApp sends an event through WebSockets to the server to register the address
- The server calls the Alchemy API to register the address with Alchemy Notify

The “send a notification” flow looks like this:

- A change happens to the registered address - they either send or receive a transaction
- Alchemy Notify calls the server webhook with the change information
- The server notifies the client through WebSockets that a change has been made to the address
- Website frontend displays the JSON response from the Websocket, inclusive of all the transaction metadata

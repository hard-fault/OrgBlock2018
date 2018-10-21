# OrgBlock2018
UCI Blockathon 2018

### Start truffle console
truffle console

### Create the app instance
OrgBlock.deployed().then(function(instance){app = instance})

### Create users
1,2,3, app.addUser("Organization", 0, 0, 0)<br />
4,5,6, app.addUser("Retail", 0, 0, 0)<br />
7,8,9,10, app.addUser("Donor", 0, 0, 0)<br />

Consider,<br />
1 - Wikipedia,  2 - Americare,  3 - Republicans<br />
4 - AWS,  5 - Walmart, 6 - Bren Event mgmt.<br />
7 - Donald<br />

### Simulate donation
app.addDonation(1,7,"Thanks Wiki",5000, {from: web3.eth.accounts[3]})<br />
>>>> fails! only PaymentGateway can create the transaction block<br /><br />

app.addDonation(1,7,"Thanks Wiki",5000, {from: web3.eth.accounts[0]}) <br />
>>>> transaction with id=1 created.<br />

### Participants validate the transaction block (validity must be 3! PGateway, Sender, Reciever)
app.getDonValidity(1)  <br />
>>>transaction_id = 1, validity must be = 1<br />

app.validateDonation(1, 1)  <br />
>>> Wikipedia acknowledges the transaction.<br />


app.validateDonation(7, 1)<br />
>>> Donald acknowledges the transaction.<br />

app.getDonValidity(1)<br />
>>> must be 3!<br />

### Check the balance
app.getAmountRecieved(1)<br />
app.getAmountRemaining(1)<br />

### Simulate expense
app.addExpense(1, 4, "Blankets", 2000)<br />
app.getAmountRemaining(1)<br />

### Participants validate the transaction block (validity must be 3! PGateway, Sender, Reciever)
app.validateExpense(1, 1)<br />
app.validateDonation(4, 1)<br />
app.getExpValidity(1)<br /><br />
>>> must be 3!<br />




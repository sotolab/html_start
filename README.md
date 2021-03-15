
# Start   

https://github.com/dappuniversity/web3_examples

https://sotoedu.herokuapp.com/


##  getBalance 
    let getbalance = await web3.eth.getBalance(fromaddress);
    let balance = web3.utils.fromWei(getbalance, "ether")

    if (DEBUG) console.log("balance : ", balance + " ETH");
    $('#message').text(" balance: " + balance + " ETH");

## send transaction

    const privateKey = Buffer.from(myPrivateKey, 'hex');
    if (DEBUG) console.log("privateKey: ", privateKey);

    web3.eth.getTransactionCount(fromaddress, (err, txCount) => {
    // Build the transaction
    const txObject = {
	nonce: web3.utils.toHex(txCount),
	to: toaddress,
	value: web3.utils.toHex(web3.utils.toWei(amount, 'ether')),
	gasLimit: web3.utils.toHex(21000),
	gasPrice: web3.utils.toHex(web3.utils.toWei('10', 'gwei'))
     }

     // Sign the transaction
     const tx = new ethereumjs.Tx(txObject);
     tx.sign(privateKey);

     const serializedTx = tx.serialize()
     const raw = '0x' + serializedTx.toString('hex')

     // Broadcast the transaction
     web3.eth.sendSignedTransaction(raw, (err, txHash) => {
	console.log('txHash:', txHash)
	  // Now go check etherscan to see the transaction!
	  })
    })  // end of txbuilder

    

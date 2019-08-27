
# Start Coinstack
Start Coinstack

Author : Soto Jang (soto1935@gmail.com)


https://blocko-1.gitbook.io/coinstack-api-reference/

https://www.blocko.io/console.html

https://sunstar.run.goorm.io


<h5>송신처  <input id="i_address" size="45" placeholder=""></input> </h5>


##  getBalance 
    client.getBalance(addr, function (err, balance) {
	    if (!err) {
			var total = CoinStack.Math.toBitcoin(balance);
			$('#i_balance').val(total);
			console.log("address: ", addr);
			console.log('total: ',total);
		}
     });

## send transaction

     let txBuilder = client.createTransactionBuilder();
     txBuilder.addOutput(toaccount, CoinStack.Math.toSatoshi(coin));
     txBuilder.setInput(fromaccount);
     txBuilder.buildTransaction(function (err, tx) {
     try {
       
      tx.sign(privateKey);
       
       let rawTx = tx.serialize();
       client.sendTransaction(rawTx, function (err) {
	 if (!err) {
	     console.log("definition: ", tx.getHash());
	     alert("거래가 완료 되었습니다..!!!");
	 }
       });
    } catch (e) {
       console.log(e)
     
      } //end of try
  
    }) // end of txbuilder

    

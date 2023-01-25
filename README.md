

  
    var config = {
        method: 'post',
        url: 'https://netconnect.bluedart.com/Ver1.10/Demo/ShippingAPI/WayBill/WayBillGeneration.svc',
        headers: { 
          'Content-Type': 'application/soap+xml'
        },
        data : data2
      };

      axios(config)
.then(function (response) {

    
        var options = {ignoreComment: true, alwaysChildren: true};
var result = convert.xml2json(response.data, options);
      // console.log(result);
      const recieve = JSON.parse(result); // get whatever we want from this parsed JSON    
        // log JSON string
      //  console.log(json);
        res.send(result);
        
//  console.log(JSON.stringify(response.data));
  
})
.catch(function (error) {
  console.log(error);
});


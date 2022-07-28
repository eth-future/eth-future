function IMPORTJSON(url,btc_address){
  try{
    // /rates/EUR
    var res = UrlFetchApp.fetch(url);
    var content = res.getContentText();
    var json = JSON.parse(content);
    if(typeof(json) === "undefined"){
      return "Node Not Available";
    } else if(typeof(json) === "object"){
      return json[btc_address]['final_balance'];       
    } else if(typeof(json) !== "object") {
      return json;
    }
  }
  catch(err){
      return "Error getting data";  
  }
}

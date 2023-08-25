
- The order of app.use() and app.get() and app.listen() and app.set() does not matter  
  
- the paths '/' and '/login' etc should match exactly for that middleware to execute  
  
- we send data to pug using res.render('pug-file-name',payload) where payload is an object which contains info we want the pug to display  
  
- In pug we use these data as #{varName} varName should exactly match as that of the payload object property  
  
- mixins are like react components  
  
- every event handler function and api requests are in the common.js file and it uses AJAX requests  
- If a Schema references another Schema then we can use Populate function to populate the current Schema with the data taken from the other Schema  
  
- for Safari flex-shrink:0 property is needed or height gets collapsed , took a long time to figure it out  
  
- Lets say Schema A references B and B references C. We need to populate A with B and B needs to populate C, so after populating A with B , we can populate B with C in .then() block , look at the post retweet route page
#  Working on login button implementation

 - Button triggers view model post function
 - Found interesting article about persitive session tokens: https://swiftsenpai.com/development/persist-data-using-keychain/
 - Base functionality of login is working. Some minor handling of changing screen when successful and presenting errors when authentication failed. 
 - Code below is useful for checking status codes in Swift Repos.
 ```
                 let status = (response as! HTTPURLResponse).statusCode
                if(status == 401){
                    let user = LoginResponse(id:UUID(),name:"",accessToken:"401")
                    callback(user)
                }
 ```
 

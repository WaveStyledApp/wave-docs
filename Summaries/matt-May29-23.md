#  Login Functionality Wrap Up
- Left to do

1. Show error on screen when login fails
    - This is done but can be visually improved
2. Make sure that we can login proper after a failed login
    - Done
3. Remove prints
    - Done
    
##Review:
    - Comment code, particularly on Swift side. and Clean it up.
    - Clean up login code on the backend
 
## Create Account

- Only difference for initial setup is create account having a seperate module for the form since Swift can only have 8-10 objects on one view, but multiple views in onw.

- Code for printing Raw Json in Swift
```
                if let jsonString = String(data: data, encoding: .utf8) {
                                    print("Raw JSON response: \(jsonString)")
                                }
```

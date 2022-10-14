
---
layout: default
nav_exclude: true
--- 

# Is NoSQL the Way?

### A Bit of an Update...

Over the past month or so, I've been delving into AWS, getting some exposure to the AWS linux terminal from EC2, and have successfully figured out how to use IAM (Identity Access Management) to give user roles access to the services I employ with my account (so users that connect can only read/write etc.).  On top of that, learning how to add databases to EC2 instances and connecting S3 buckets as well.

Still researching that data, and I plan to upload my notes when I complete the full deal. 

### Separating Images from User data

The biggest issue with the current configuration app (outside of it being purely local) is how we store user data. 

**Right Now**, we store it in a RDS that stores the wardrobe, outfits, and images for each user, with each table identified using the userID. 

**Issues**: Storing images as a byte string is extremely inefficient and waste computational time and space. Also, each user has now 3 tables that have to be consistent and managed properly. Furthermore, for large wardrobes, each image has to be rendered using that byte string on demand and that is VERY SLOW.

### Solution: S3

Store Images in a dedicated bucket on S3 and keep a *reference* to that data stored in an actual table. This ensures fast retrieval of items and images can be displayed using an async call. The benefit of S3 is that it is replicated over availability zones, so worrying about fault tolerance and corruption is handled for us alongside general security.

The Library AWS amplify allows us to return an S3 image on demand. Given a userID (which is already propagated in the App Context) and the clothingID, retrieval should be very easy.

https://docs.amplify.aws/ui/storage/s3-image/q/framework/react-native/

**Adding Images**

Each EC2 instance can instantiate an S3 bucket (which is just a pool of data). On User Creation, API call to create a folder with the userID as its name. On image upload using AWS-Amplify, add it to the folder. This ensures mutual exclusiveness and easy navigation to a user's items. 

[Upload Images &amp; Videos to AWS S3 Bucket in React Native - instamobile](https://instamobile.io/react-native-tutorials/react-native-aws-s3/)

Security - Could look into modifying user permissions to only access folders that belong to them (using a S3 bucket policy) but since a userID only knows its own ID, it can only read their own data which can avoid that potential roadpath.

**Caching**

On bootup or login on the same devices, images should not need to constantly be retrieved from the S3 bucket. Caching is the solution and we can store the wardrobe images on the device and use that in outfit generation for quick rendering and performance.

Only when the cache is empty, then update from the database. 

[Caching images in React Native: A tutorial with examples - LogRocket Blog](https://blog.logrocket.com/caching-images-react-native-tutorial-with-examples/)

**Server Caching** 

CloudFront is an AWS service that allows data from a service outside an availability zone to be cached on that local server to lower retrieval latency. Only when a write happens, is the server cache updated. This is mostly relevant for international users, since our servers wil be US based. (Not currently relevant but important to note)

---

# Now the main point, why NoSQL?

AWS does provide support for Relational Database systems, but I don't think they are good enough for the type of data we want to store. We want quick retrieval of large amounts of data, and keeping separate tables with the user data requires unnecessary joins that slow down query time and efficiency. 

### Dynamo or some NoSQL DB

NoSQL Databases are similar to key value stores, so we just ask for the user information and retrieve the whole object we are looking for. This is PERFECT for wardrobe needs, as that is the *first* thing the users want to see when they open the app.

**Amazon Shopping Order Analogy**

I think wardrobes are analogous to shopping orders, where we are storing a set of items that the user has in their "cart" but without the payment stuff. This article was a solid eye opener:

https://www.alexdebrie.com/posts/dynamodb-single-table/

The article also includes pros and con of the single table design. 

![Dynamodb -- Users & Orders in single table](https://user-images.githubusercontent.com/6509926/73772626-1e4f0780-4746-11ea-84f4-1490119d7cd6.png)

In Dynamo, we have a primary key, and that key points to the data it stores. This model is exactly what we want for a wardobe.

**Proposal for Transition**

userID is naturally the partition key (which allows for quick searching like a hashmap). The Sort key will be the wardrobe items of that user. Each clothing items will have the same set of attributes similar to the ORDER rows in the image above. 

Stores the clothingID, color, weather/occasions in a SET datastructure, userID for extra security, and the REFERENCE URI for the image the item associates to.

In S3, URI images are used to retrieve data we want, and this works perfectly with how React-Native uses images on app running. 

Similar to the PROFILE row, we can have relevant information on the user like their preferences, name, etc. 

**Lastly, Outfits**

Outfits are sets of clothing items, so Outfits can simply be rows on the datatable that are a set of the Clothing Item sort keys.

## Conclusion

Transitioning to a single table database system might be tough to modify and organize however, but for the needs of the app, its quick retrieval of relevant data that we need. 

Images are async operations, so they will load as the operations so. 

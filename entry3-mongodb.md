# Nov 20 2015
## MongoDB CSharp Driver 2.0 usage

### Basic Setup of access to a database
Note that CourtWebsite is a POCO class that I am storing in the database. I am not just storing generic BsonDocuments.
```csharp
var client = new MongoClient("mongodb://dev-web-ext");
var database = client.GetDatabase("CourtCruft");
var collection = database.GetCollection<CourtWebsite>("CourtWebsites");
```

### Get all documents. 
You cannot use an empty CourtWebsite() as the filter parameter. You have to use a blank BsonDocument. 
```csharp
var documents = await collection.Find(new BsonDocument()).ToListAsync();
``` 

### Update a record, and an example of how to cheat with async
Using this idiom allows you to do all the async methods mongo forces you to use in a synchronous method. 
Here I have a courtWebsite object already filled out with the updated data. I create a filter on the Id
and then update. 
```csharp
var filter = Builders<CourtWebsite>.Filter.Eq(s => s.Id, courtWebsite.Id);
Task.Run(async () =>
{
	await collection.ReplaceOneAsync(filter, courtWebsite);
}).Wait();
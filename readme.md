# Dublin Bikes

![](https://seda.college/blog/wp-content/uploads/2018/10/dublin-bikes-1.jpg)

### Data Acquisition:

We acquired the live data of dublin bikes from the API : https://developer.jcdecaux.com/#/opendata/vls?page=getstarted .
It have follwing attributes : number, contract_name, name, address, position, banking, bonus, bike_stands, available_bike_stands, available_bikes, status, last_update.
It is the information of different cycle stands with their location and infromation regarding bike availability and total number of bikes that stand holds.
From all this data we can look at the pattern of bikes being used on a perticular time of day, we can look at the stands near the colleges and see how the movement of bikes are happening there and create insights out of it
 
### Transforming the data:

After observing the data, last_update is in timestamp - milisecond which we will convert to seconds and then use datetime library to convert it into human readable format.
We also retrieved coordinates from position columm, extracted it into two different columns (latitude, longitude) and then created a reverse geo function to extract the location using Nominatim API : https://nominatim.org/release-docs/latest/api/Reverse/.

### Loading Data to mongo db server:

We created a database on mongo db and connected it to our project to upload the data we are fetching from live API. We used pymongo library to connect to the database through mongoclient string. we converted the data frame to dictionary before uploading to the mongo as it takes data in that format.

### Creating Pipeline:

We created a pipeline to perform all the steps which includes : 

#### Data Acquision : 
created a function to collect data from API convert it into json and then Data Frame
#### Data Transformation : 
Transformed time and poition columns using datetime library and Nominatim API.
#### Data Upload to mongo db : 
Create a database in mongodb console and connected it to our project.

we used while loop and defind a time of 10 hours to fetch the data with a sleep time of every 30 mintues. We fetched the data of every 30 minutes and got the data uploaded in our database.

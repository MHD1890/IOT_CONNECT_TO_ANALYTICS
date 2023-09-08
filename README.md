# IOT_CONNECT_TO_ANALYTICS
This repository for connect your IOT Core to IOT Analytics
___________________________________________________________

![WhatsApp Image 2023-09-08 at 15 24 54](https://github.com/MHD1890/IOT_CONNECT_TO_ANALYTICS/assets/140581107/30fff817-f4ee-42f2-bc72-e133de9ec84a)

____________________________________________________________
Fist you need a module to connect IOT Core, for example iam using ESP32 to export a data {Temperature and Humidty}, next you need and make sure it's connected to mqtt aws.

![1](https://github.com/MHD1890/IOT_CONNECT_TO_ANALYTICS/assets/140581107/d46bdf7a-8d4c-4f01-9271-452279ae2079)

Next you need create a message routing > rules > and choose create 

![2](https://github.com/MHD1890/IOT_CONNECT_TO_ANALYTICS/assets/140581107/17d33882-5675-4210-b1fe-e52f4cc94402)

And give the name for example my name MyESP32 and the data iam using {Collecting data from MyESP32 MQTT Client

![3](https://github.com/MHD1890/IOT_CONNECT_TO_ANALYTICS/assets/140581107/70fe15aa-0f94-4fb0-b085-3e1d61a1dcdd)

Next in SQL Query you need You have to fill in the SQL data according to the output message from MQTT, for example MyESP is ouput Temperature anfd Humidty
And click on next choose Action 1 (Replubish to AWS IOT TOPIC) and for example iam using MQTT LINK is "temp/rule"

![4](https://github.com/MHD1890/IOT_CONNECT_TO_ANALYTICS/assets/140581107/18d7eb18-c490-4600-883b-1afa657ee8b9)

Next in action 2 you choose IOT Analytics, for this example Iot Analytic iam export to S3 Bucket, lest try this tuotrial "How to create bucket in s3 Bucket"
________________________________________________________________________________________________________________________________________________________________
First you need give unic name for your bucket for example my name bucket is "testerbucketdemoanalytic", and choose your region

![6](https://github.com/MHD1890/IOT_CONNECT_TO_ANALYTICS/assets/140581107/b2ce320e-3766-451b-a4ff-257beb599089)


Next uncheck all Block all public access and also the I acknowledge button

![7](https://github.com/MHD1890/IOT_CONNECT_TO_ANALYTICS/assets/140581107/9c956b2a-a390-4aff-aa09-96db0f9f7780)

Next choose create bucket, press button your bucket and choose permision 

![8](https://github.com/MHD1890/IOT_CONNECT_TO_ANALYTICS/assets/140581107/4b9b601d-25b1-45c3-96c1-336fcd7a4c78)

Next you need edit a Bucket Policy 
{DATA JSON POLICY HERE}
{
   "Version":"2012-10-17",
   "Statement":[
     {
       "Sid":"PublicRead",
       "Effect":"Allow",
       "Principal": "*",
       "Action":["s3:GetObject","s3:GetObjectVersion"],
       "Resource":["arn:aws:s3:::YOUR-NAME-ARN-BUCKET-HERE/*"]
     }
    ]
}
{END OF DATA JSON}

![9](https://github.com/MHD1890/IOT_CONNECT_TO_ANALYTICS/assets/140581107/76ee51a3-8c17-4324-8d8d-1952ac089d8c)

And click save Changes,

__________________________________________________________________________________________________________________

Next, if you have successfully created an IoT Topic and IoT Analytics, you can go to MQTT CALIENT TESTER IN AWS fill in your mqtt link, for exmaple ini belo  iam use "temp/rule" like this ]

![11](https://github.com/MHD1890/IOT_CONNECT_TO_ANALYTICS/assets/140581107/36ccbba0-9c1d-4d06-8add-ef6ed3e94601)

And you can check your MQTT Local for your Link MQTT Like this 


![12](https://github.com/MHD1890/IOT_CONNECT_TO_ANALYTICS/assets/140581107/ae33d467-c153-45b1-a433-a3dee08473c9)

Next, check your data bucket, whether your IoT log data has been filled into the S3 Bucket, if so, it will produce output like this

![13](https://github.com/MHD1890/IOT_CONNECT_TO_ANALYTICS/assets/140581107/719507c0-5591-4958-a3d3-d4d79446377b)

Lastly, you also see your log data in IOT Analytic like this and choose button create dashboard, you need give name for your dashboard

![15](https://github.com/MHD1890/IOT_CONNECT_TO_ANALYTICS/assets/140581107/720daaf0-1dac-45ef-82d3-4acfecbf65dd)


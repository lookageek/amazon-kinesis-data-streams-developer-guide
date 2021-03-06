# Step 1: Create a Stream<a name="learning-kinesis-module-one-create-stream"></a>

In this step, you create the stream you'll be using in subsequent steps\.

**To create a stream**

1. Open the Kinesis console at [https://console\.aws\.amazon\.com/kinesis](https://console.aws.amazon.com/kinesis)\.

1. Choose **Go to the Streams console**\.

1. In the navigation bar, expand the Region selector and choose a Region\.

1. Choose **Create Kinesis stream**\.

1. Type a name for your stream \(for example, **StockTradeStream**\)\.

1. Type **1** for the number of shards, but leave **Estimate the number of shards you'll need** collapsed\.

1. Choose **Create Kinesis stream**\.

On the **Kinesis streams** list page, the status of your stream is `CREATING` while the stream is being created\. When the stream is ready to use, the status changes to `ACTIVE`\. Choose the name of your stream\. In the page that appears, the **Details** tab displays a summary of your stream configuration\. The **Monitoring** section displays monitoring information for the stream\.

## Additional Information About Shards<a name="learning-kinesis-module-one-create-stream-info"></a>

When you begin to use Kinesis Streams outside of this learning module, you may need to plan the stream creation process more carefully\. You should plan for expected maximum demand when you provision shards\. Using this scenario as an example, U\.S\. stock market trading traffic peaks during the day \(Eastern time\) and demand estimates should be sampled from that time of day\. You then have a choice to provision for the maximum expected demand, or scale your stream up and down in response to demand fluctuations\. 

A *shard* is a unit of throughput capacity\. On the **Create Kinesis stream** page, expand **Estimate the number of shards you'll need**\. Type the average record size, the maximum records written per second, and the number of consuming applications, using the following guidelines:

**Average record size**  
An estimate of the calculated average size of your records\. If you don't know this value, use the estimated maximum record size for this value\.

**Max records written**  
Take into account the number of entities providing data and the approximate number of records per second produced by each\. For example, if you are getting stock trade data from 20 trading servers and each generates 250 trades per second, the total number of trades \(records\) per second is 5000/second\. 

**Number of consuming applications**  
The number of applications that independently read from the stream to process the stream in a different way and produce different output\. Each application can have multiple instances running on different machines \(i\.e\., run in a cluster\) so that it can keep up with a high volume stream\.

If the estimated shards shown exceeds your current shard limit, you may need to submit a request to increase that limit before you can create a stream with that number of shards\. To request an increase to your shard limit, use the [Kinesis Streams Limits form](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-kinesis)\. For more information about streams and shards, see [Kinesis Streams](amazon-kinesis-streams.md) and [Managing Kinesis Streams Using Java](working-with-streams.md)\.
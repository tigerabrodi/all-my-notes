# Acknowledgements

Thanks to the amazing people who gave me feedback and helped this article come to life.

- ...

# Introduction

In this article, we'll cover data sharing, how it's changing and where it is heading.

We'll also cover why Bobsled is the ultimate solution for data sharing, and how it will help the world move forward by coming to decisions much faster than they ever have.

# Data sharing

Companies share data with other companies. Especially as companies grow, different types of data serve as the foundation to learn things and come to decisions.

- The company that shares its data is the data provider.
- The one that uses the shared data is the data consumer.
- A **share** is the term for the sharing of data that gets done between a provider and consumer.

Generally speaking, three types of data form the foundation for business operations and analytics within many enterprises:

- First-party data is data a company can collect from its own sources: For example, from interactions with customers and prospects.

- Second-party data is data you acquire from a trusted partner: For example, data from a SaaS vendor or feedback from customers.

- Third-party data is data collected from external sources that don’t have a relationship with your business. Examples: demographic, weather, and financial market data.

First-party data are direct relationships with the customer compared to the other types of data.

The first-party and second-party data aren't the main problems, third-party data is. Sharing data to external sources or collecting them from external sources.

## Explosive growth of third-party data

The demand for third-party data has blown up over the past years. According to [Explorium: 2022 State of External Data](https://www.explorium.ai/blog/2022-state-of-external-data-procurement/):

- The market for 3rd party data is roughly $100b a year, growing at
  10-15% CAGR.
- 52% of companies surveyed said they were purchasing data from 5 or
  more paid or public sources - this is up from 9% in 2021.
- 41% of companies spend more than $500,000 annually on external
  data, with many spending well into eight or nine figures.

# The traditional problems with data sharing

Let's go over the traditional problems with data sharing before we dig into the problems of modern data sharing. The problems span from manually doing & customizing things to building and maintaining custom pipelines.

A data file is emailed from a provider to a consumer:

- Emails aren't secure.
- It is hard to edit and undo things with emails.
- There can be limitations around sending very large files.

Through File Transfer Protocol (FTP), data files are shared and downloaded between two computers or via the Internet:

- FTP is not secure
- FTP is unreliable, it can take a lot of time to develop, maintain and troubleshoot scripts
- FTP is outdated, it can't grow with your organization as you need more features and security

An API (Application programming interfaces) is used to initiate and manage the data transfer:

- Data is being stored at least twice.
- There is a need for API management. Constant development and fixing broken things that require a lot of time.
- Issues with keeping copies of data set in sync and correct.

ETL (Extract, Transform, Load) software extracts data from the provider’s database, transform it into a format that fits for consumption, and then loads it into the consumer’s database:

- Lack of ETL developers.
- Takes time to develop (we're speaking of weeks to months) and then maintaining & fixing broken things.
- Data formats changing over time.

The provider stores a copy of the data and provides the consumer with credentials for accessing it:

- Manual process
- Something can go wrong when sharing credentials
- If the provider needs to share data with multiple consumers, this process won't scale

I mentioned a few problems of the common traditional ways of sharing data. You can probably understand why modern data sharing solutions were built. The traditional ways of sharing data all contained problems and pain.

# The vision

In today's age consumers are on multiple different platforms and clouds (Amazon, Google, Microsoft, Databricks, Snowflake...).

The vision:

- Deliver data to the consumer's platform of choice.
- Make it easy for consumers to try new data.
- Deliver data quickly and effortlessly.
- Be flexible to customize the delivery as requirements change.
- Ensure delivery is secure and reliable.

# Modern data sharing

There are multiple modern ways of sharing data in today's age:

- AWS Data Exchange (both S3 and Redshift)
- Snowflake Data Sharing and Snowflake Marketplace
- Delta Sharing
- Azure Data Share
- Google Datashare

In particular, Snowflake is very famous for having removed the pain that came with sharing data traditionally.

## The problems

So, what are the problems with the modern solutions mentioned? Hasn't the problem with data sharing been solved? Not quite.

Sharing data to external sources hasn't fully been solved, and the vision isn't a reality yet.

- Cloud platforms are building walled gardens. Their data is trapped within the cloud providers.
- In order to share data between different platforms, providers need to build their own integrations. For an instance if they want to share data from Google to Amazon.
- Building and managing custom integrations is expensive
- By always having pipelines to develop and maintain, providers can't keep up with the demand.
- Custom pipelines will always be different when developed, leading to another point of failure.

# Just Bobsled It

What if you didn't have to move your data to a platform or build custom pipelines to share it to a provider that is on a different platform than you?

What if you could just with a few clicks share data to any cloud or platform, fulfilling the vision we mentioned?

That's right, Just Bobsled It. Just use Bobsled and sled your data.

Bobsled isn't a feature, it is THE data sharing product, the ultimate solution for data sharing.

- Bobsled is cloud & platform agnostic. Share data to any cloud or platform without developing custom pipelines nor having to move your data to different platforms.
- Bobsled is quick & flexible. Share different formats of data in a single delivery, customize existing deliveries, automate deliveries to run on a schedule & much more.
- Bobsled is designed to enable providers to deliver to any customer, regardless originating sources or delivery requirements.

## Revolutionary results

By choosing to sled your data with Bobsled, you can imagine the revolutionary results as outcome.

- Consumers get to value faster. There is no need for any custom pipelines to be built, and by delivering the data to the consumer's platform of choice, consumers can begin working with the data right away and avoid building ingestion pipelines (pipelines to get the data onto their platform).
- The consumer experience gets improved.
- Sharing data is cheaper. There is no need to have a whole team maintaining a pipeline, on either the consumer or provider's side.
- Let's providers meet requirements they couldn't do before due to the technical cost hence they can reach new customer segments.
- Improved reliability, governance and security.
- By removing the friction of having to maintain pipelines, technical teams can focus on building new and improved data products.

# Conclusion

Just Bobsled It.

That is the conclusion, the ultimate solution for data sharing is to sled your data through Bobsled.

Bobsled will help companies exchange data faster, get to value faster, come to decisions faster and help the world move forward at a faster pace..

So, I'll share my journey into and through Cloud, learning Amazon Web Services. I want to point out that I'm writing this as I'm learning, so you could sort of describe it as **Blog-driven development** if you wish.

# Initial impression

I heard about **The Cloud Resume Challenge** from my friend [Andy](https://twitter.com/EastlondonDev).

My initial impression of **The Cloud Resume Challenge** was great. I was worried it was gonna be some other theoretical read about AWS, and not something that is pragmatic.

This is what the challenge is about, it is extremely pragmatic, because all it really is in the end, is you building stuff given project specs.

Though, I will say it contains more than just project specs, and I do think if you're going in with the intention of transitioning into tech and becoming a Cloud Engineer, it is really good, because it also covers how others have gone through it and transitioned into becoming Cloud Engineers.

I won't lie, it is motivating.

To explain it in short, the book contains Chunks you should go through, which is basically all a part of building a fullstack project. You could describe each Chunk as a mini project in itself, but if you do finish all the Chunks, you will have a very comprehensive project to showcase in the end, and will have learned a lot of course.

# My Plan

I plan on trying to go through this resource quite quickly, and afterward build a fullstack side project myself with Remix and AWS services.

I've always been a fan of trying to take the learnings from a resource, and then applying those to a whole new separate side project.

It is gonna be fun!

# Setting up AWS

Before beginning anything, you will have to set up AWS. The book recommends a different approach, though, the approach I took I found easiest and quite straight-forward. Also, to mention, I'm using **IAM Identity Center** which is brand new, it was released like last month roughly as I'm writing this.

1. Create a root account with AWS.

2. Make sure to verify your account and register a valid credit card. This part is a bit annoying, that you've to register a credit card to be able to use many of AWS services, but I get it, all good.

3. Set up AWS Control Tower. If you need emails for new accounts, you can you the email subaddressing trick. This way you can use a different email, but the destination of mails is still your main account. It is also called the plus sign trick. For example, if John needs to create an account for auditing: **john+audit@gmail.com**. Even though this is a different email, the mails will be sent to **john@gmail.com**.

4. Activate IAM user and role access: https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/control-access-billing.html#billing-activate-iam-access.

5. Use AWS SSO to sign-in into different accounts whenever you wish. You will get an invitation in your email.

6. Create a **testing** and a **production** organizational unit (OU) in your organization using the Control Tower, you can put them at the root level.

7. Create an account in both OUs, one will be used for testing/development, and one will be used for the production, meaning the live environment of the project which is public for anyone to visit on a specific domain. Here again, for the emails of the accounts, you can use the subaddressing trick.

You may encounter an error when creating the accounts, that is because you're logged in as the root account, or at least was for me, You will have to switch to the master account. The account that is created when setting up the control tower, it can be found in the root of your organization.

Switch account by using AWS SSO, the easiest way to do so.

# Confession

I'm writing this as I'm done with the course, in the end, I decided to go with simply creating an IAM user and using that for the project, both for development and production. My goal here was to get into Cloud and learn AWS, and I find myself moving faster by just using an IAM user for the entire project.

I did follow the least privilage principle, and didn't give my IAM user more permissions than necessary though.

# AWS Cloud Practitioner Essentials

The other thing you will have to do is the **AWS Cloud Practitioner**. Now, I didn't do the exam, because I'm not looking for certifications, as I'm already working as a developer and my goal is to learn AWS pragmatically.

Though, if you're looking for your first Cloud Engineering job, I can imagine it is worth getting a certification.

I went through this course: [AWS Cloud Practitioner Essentials](https://explore.skillbuilder.aws/learn/course/134/aws-cloud-practitioner-essentials).

I also shared my notes here: [AWS Cloud Practitioner](https://tigerabrodi.blog/aws-cloud-practitioner).

# Resume

We're building a site that displays our resume and also keeps track of the visitor count. This is really quick to build with of a bunch of other technologies, but the goal with this challenge is to learn AWS, so we're just using AWS services here.

# Chunk 1

This chunk was quite straight forward. I built a resume in HTML and CSS that was deployed on as a Static S3 Website. I then made sure the site uses `https` for security and had to use Amazon CloudFront.

The last step was to point a custom DNS domain name to the CloudFront distribution, but I didn't do that part as I don't feel the need here to setup a custom domain name, which also includes buying a new one.

# From here

From here (beginning of chunk 2) honestly I just went ahead and built the whole thing. I skimmed all the chunks of the challenge and realised I'm not too far away from building it all lmao.

Though I skipped the part of using a custom domain with DNS, since this is just a resource I'm going through, I'm trying not to do it strictly, but rather get my AWS learnings and then move on to building a real fullstack app.

## The URL

I won't share the deployed URL as I don't want people to start visiting the site and end up actually paying something because of this project to AWS. FYI it is a generated one by Amazon CloudFront.

## Frontend

The frontend code can be found here: https://github.com/narutosstudent/cloud-resume.It was built with HTML, CSS and JavaScript. I'm using Lambda Function URLs to trigger the Lambda.

The frontend is deployed on S3 as a static site. I configured an Amazon CloudFront distribution to serve HTTPS (secure) requests for the site, otherwise it'd be reachable via HTTP only which isn't secure.

CloudFront generated a URL for me. It also uses its edge cache to cache the files, hence every time I update the files in my S3 bucket, I've to invalidate the files. Honestly, it'd be smarter to check which files change, but I'm cool with how I approached it since its just 3 files.

The code for my Github Actions: https://github.com/narutosstudent/cloud-resume/blob/main/.github/workflows/deploy-s3.yml.

The Github Actions I won't was a bit tricky to figure out, but I was able to make it work in the end, especially the part where you want to exclude and include certain files when syncing the bucket was super tricky because the answers online differed. One of those simple things that annoy the living shit out of you. Configuring AWS was really straightforward though, it made me happy.

## Backend

The backend code can be found here: https://github.com/narutosstudent/lambda-resume-dynamodb-backend.

I had to build the API using DynamoDB and Lambda. I also enabled Lambda Function URL so I can just trigger the Lambda by calling the URL, instead of using a gateway. It is quite new from what I heard, works like a charm.

Writing the Lambda itself wasn't too difficult, you're just exporting a handler function, but DynamoDB was hell of a pain, because at first I tried figuring out how to use it without the `DocumentClient` (was reading the wrong docs) which was tricky.

Using the `DocumentClient` and referring to this cheatsheet made things more straightforward: https://dynobase.dev/dynamodb-nodejs/. `DocumentClient` simplifies working with DynamoDB items.

When it comes to the Github Actions, this was a great read: https://dev.to/nobleobioma/deploy-node-js-to-aws-lambda-using-github-actions-5a82/. I had to tweak some of the stuff since it is outdated.

Reading the code you can probably see how I went with a quite simple & lazy approach that at least works, I'm just not a fan of doing things correctly when going through resources, I try more to learn quickly and apply the stuff on real side-projects.

# Conclusion

The Cloud Resume Challenge is great, it is more or less a project spec with helpful resources. It is hard and the learnings come from you, that's what I love about it, it is very practical.

If you're looking to land a job in the field of cloud engineering, it is extremely good as it includes real use-cases and many of the stories there are motivating.

This is for you if you're looking to get started with your cloud journey.

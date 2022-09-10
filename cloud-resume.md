So, I'll share my journey into and through Cloud, learning Amazon Web Services. I want to point out that I'm writing this as I'm learning, so you could sort of describe it as **Blog-driven development** if you wish.

# Initial impression

I heard about **The Cloud Resume Challenge** from my friend [Andy](https://twitter.com/EastlondonDev).

My initial impression of **The Cloud Resume Challenge** was great. I was worried it was gonna be some other theoretical read about AWS, and not something that is pragmatic.

This is what the challenge is about, it is extremely pragmatic, because all it really is in the end, is you building stuff given project specs.

Though, I will say it contains more than just project specs, and I do think if you're going in with the intention of transitioning into tech and becoming a Cloud Engineer, it is really good, because it also covers how others have gone through it and transitioned into becoming Cloud Engineers.

I won't lie, it is motivating.

To explain it in short, the book contains Chunks you should go through, which is basically all a part of building a fullstack project. You could describe each Chunk as a mini project in itself, but if you do finish all the Chunks, you will have a very comprehensive project to showcase in the end, and will have learned a lot of course.

# Setting up AWS

Before beginning anything, you will have to set up AWS. The book recommends a different approach, though, the approach I took I found easiest and quite straight-forward. Also, to mention, I'm using **IAM Identity Center** which is brand new, it was released like last month roughly as I'm writing this.

1. Create a root account with AWS.

2. Make sure to verify your account and register a valid credit card. This part is a bit annoying, that you've to register a credit card to be able to use many of AWS services, but I get it, all good.

3. Set up AWS Control Tower. If you need emails for new accounts, you can you the email subaddressing trick. This way you can use a different email, but the destination of mails is still your main account. It is also called the plus sign trick. For example, if John needs to create an account for auditing: **john+audit@gmail.com**. Even though this is a different email, the mails will be sent to **john@gmail.com**.

4. Use AWS SSO to sign-in into different accounts whenever you wish. You will get an invitation in your email.

5. Create a **testing** and a **production** organizational unit (OU) in your organization using the Control Tower, you can put them at the root level.

6. Create an account in both OUs, one will be used for testing/development, and one will be used for the production, meaning the live environment of the project which is public for anyone to visit on a specific domain. Here again, for the emails of the accounts, you can use the subaddressing trick.

You may encounter an error when creating the accounts, that is because you're logged in as the root account, or at least was for me, You will have to switch to the master account. The account that is created when setting up the control tower, it can be found in the root of your organization.

Switch account by using AWS SSO, the easiest way to do so.

# AWS Cloud Practitioner Essentials

The other thing you will have to do is the **AWS Cloud Practitioner**. Now, I didn't do the exam, because I'm not looking for certifications, as I'm already working as a developer and my goal is to learn AWS pragmatically.

Though, if you're looking for your first Cloud Engineering job, I can imagine it is worth getting a certification.

I went through this course: [AWS Cloud Practitioner Essentials](https://explore.skillbuilder.aws/learn/course/134/aws-cloud-practitioner-essentials).

I also shared my notes here: ...

# Chunk 1

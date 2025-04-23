# Linking Data

Before we take a look at how we actually link data in Toca, let's first revisit why we might want to link table data.

* **Avoid Redundancy:** Instead of repeating user information for every order, you just link them. If a user's details change, you update them once, and it reflects everywhere.
* **Data Integrity:** Relationships help keep your data consistent and accurate, maintaining the links between each row of data.
* **Powerful Queries:** You can easily find all orders by a specific user or all users who ordered something from a specific category.
* **Better Organization:** Relationships make your app's data structure clearer and easier to understand as it allows you to model the data more closely to the real world representation of the data.

# Connecting Your Data: Relationships in Toca

Imagine you're building an eCommerce app where users can buy items and get their orders delivered to them. You'd have products, you'd have users, their orders and their addresses. Each user has an address, and each user might have ordered multiple products. How do you represent this connection in Toca? That's where **relationships** come in!

## What are Relationships?

The table relationships you find in Toca are heavily inspired by, but not _exactly_ the same as, relationships you find in Databases. A relationship is a link between a row of data in one table to another row of data in a different table. The link is represented by the ID of the row you are linking to. This will be easier to visualise with an example so let's build on our eCommerce use case!

Here we have our Users table that we have already created:
| Id  | Name            | Email address        | Profile picture | Date of birth |
| :-- | :-------------- | :------------------- | :-------------- | :------------ |
| 1   | Alan Turing     | alan@computers.inc   | 💻              | `1912-06-12`  |
| 2   | Tim Berners-Lee | tim@worldwideweb.com | 🌐              | `1955-06-08`  |
| 3   | Linus Torvalds  | linus@linux.net      | 🐧              | `1969-12-28`  |

Now, if we have a table of addresses below:
| Id | Address Line 1 | Address Line 2 | City | Area Code |
| :-- | :-- | :-- | :-- | :-- |
| 50 | Bletchley Park | Milton Keynes | Buckinghamshire |  MK3 6EB |
| 42 | CERN 1211 | Esplanade des Particules 1 | Geneva | 1217 |
| 64 | University of Helsinki | Yliopistonkatu 4 | Helsinki | 00100 |

How do we link the two tables together so that each user is associated with an address?

Well, normally you should model your relationships as closely to real life, so in the context of our eCommerce project, our users will come first and then the addresses. So that means we should have a users row _before_ we have an addresses row, this means that our Addresses table should link to a user. You wouldn't have an address before having a user, would you? So if you think about the order the data is created in, first a user would sign up which would insert a new user into our Users table and then that user would configure their delivery address which would then insert a row into our Addresses table with the associated user ID.

Therefore our Addresses table should be modified to have a new column on it called "Associated User" and the values in this will be the corresponding ID of the user that the address relates to! Let's make that change and see what our table now looks like:

| Id | Address Line 1 | Address Line 2 | City | Area Code | Associated User |
| :-- | :-- | :-- | :-- | :-- | :-- |
| 50 | Bletchley Park | Milton Keynes | Buckinghamshire |  MK3 6EB | 1 |
| 42 | CERN 1211 | Esplanade des Particules 1 | Geneva | 1217 | 2 |
| 64 | University of Helsinki | Yliopistonkatu 4 | Helsinki | 00100 | 3 |

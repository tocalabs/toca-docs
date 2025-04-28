# Linking Data

Before we take a look at how we actually link data in Toca, let's first revisit why we might want to link table data.

* **Avoid Redundancy:** Instead of repeating user information for every order, you just link them. If a user's details change, you update them once, and it reflects everywhere.
* **Data Integrity:** Relationships help keep your data consistent and accurate, maintaining the links between each row of data.
* **Powerful Queries:** You can easily find all orders by a specific user or all users who ordered something from a specific category.
* **Better Organization:** Relationships make your app's data structure clearer and easier to understand as it allows you to model the data more closely to the real world representation of the data.

# Connecting Your Data: Relationships in Toca

Imagine you're building an eCommerce app where users can buy items and get their orders delivered to them. You'd have products, you'd have users, their orders and their addresses. Each user has an address, and each user might have ordered multiple products. How do you represent this connection in Toca? That's where **relationships** come in!

## What are Relationships?

The table relationships you find in Toca are heavily inspired by, but not _exactly_ the same as, relationships you find in databases. A relationship is a link between a row of data in one table to another row of data in a different table. The link is represented by the ID of the row you are linking to. This will be easier to visualise with an example so let's build on our eCommerce use case!

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

The first thing to do is think about the real world relationships in the data we are representing. In this case, it is most common for multiple people to be associated with a single address. So when we take that into account, it makes the most sense to add an "Associated Address" field to our User's table. It's also good to think about how you want to display your data. If you are building an App and you might have a Profile page which contains all the details about your user, the Address is something that you'd want listed on the Profile page so the User is the parent and the Address is the child.

| Id  | Name            | Email address        | Profile picture | Date of birth | Associated Address |
| :-- | :-------------- | :------------------- | :-------------- | :------------ | :--- |
| 1   | Alan Turing     | alan@computers.inc   | 💻              | `1912-06-12`  | 50 |
| 2   | Tim Berners-Lee | tim@worldwideweb.com | 🌐              | `1955-06-08`  | 42 |
| 3   | Linus Torvalds  | linus@linux.net      | 🐧              | `1969-12-28`  | 64 |

![How our entities are linked](/src/assets/book/conceptual_links.png)

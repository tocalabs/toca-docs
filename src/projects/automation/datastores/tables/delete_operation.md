# Delete Operation
To help prevent orphaned data in certain situations there is the ability to include delete operations for `One-To-One` and `One-To-Many` table relationships.

## None
The NONE option prevents the deletion of child rows. For example, if a customer references an address, deleting the customer will have no impact on the address row referenced.

## Cascade
The CASCADE option deletes all rows in the child table that have matching rows in the parent table ONLY IF there is no other reference to that child row in this or any other table in the datastore. For example, if a customer references an address, attempting to delete the customer will also delete the address associated with that customer provided no other customer references the address.

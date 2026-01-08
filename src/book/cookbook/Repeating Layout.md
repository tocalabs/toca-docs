## Using a Repeating Layout to display data

The Repeating Layout app component allows you to easily repeat over **a table of data**. The component allows you to drag and drop other components into it which can then use context from that particular row of the table. For example:

**1. Add a Repeating Layout**

- Insert a Repeating Layout.
- Select a Data Source for the Repeating Layout, for example, the **Cities** table.
- Customize the component as needed. You might add Pagination and style it accordingly.
  - Example styling: Size: Small, Shape: Round

![Image 1](<../../assets/cookbook/repeating-layout/Image1.png>)

**2. Add two Flex Layouts inside the Repeating Layout**

Add two Flex Layouts:
- **First**: Serves as a general container for other components.
- **Second**: Displays data from the table (you may also use a Responsive Grid component).
  - For this example, adjust the width of the second Flex Layout to 25% to suit the display goals.

**3. Add a Text component inside the second Flex Layout**

- Inside the second Flex Layout, add a **Text** component. 
- Go to **Variable > Context** to select the field from the table you want to display (e.g. **City**). 

![Image 2](<../../assets/cookbook/repeating-layout/Image2.gif>)

**4. Duplicate the second Flex Laoyut for additional data**

- Duplicate the **second Flex Laoyut containg Text component** to display more fields. 
- Repeat the steps above and update the **Variable > Context** selection to show other values like **Country**, **Population**, and **Famous Landmark**.

![Image 3](<../../assets/cookbook/repeating-layout/Image3.gif>)

**5. Adjust visual styling**

Make the following enhancements within the second Flex Layout (the one containing other layouts):
- Spacing between the flex layouts 
- Background colour (e.g. #f8f2e5)
- Bottom Margin 
- Padding 
- Radius: 4 px
---
A header row was also added to provide clear labeling, so you could see the **final result of the configuration below**:

![Image 4](<../../assets/cookbook/repeating-layout/Image4.png>)
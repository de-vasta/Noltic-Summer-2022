# #2 - Configuration

[Homework details](https://docs.google.com/document/d/1LrnpztkJL7kwjLea4Oc4dhPAlK_NPoHmFzwC3-cQGZ4/edit?usp=sharing)

-----
<details>
<summary>Plot Part</summary>
Feet co. is a #1 real estate agency in the Sherwood forest. It’s business is growing fast and it requires the power of Salesforce to build a powerful solution to satisfy the needs of its agents and all the furry magical customers it has.
The company’s CEO Mrs. Nutsy thinks that you are a great candidate for a Position of Head of Development department at Squirrel Feet co.
Your first task is to build a data model which would allow agents to enter Property information and also manage its residents. After that you will configure the UI for agents which show relevant information about properties and to allow them to manage it.
Mr. Nutsy has already read some articles about Salesforce therefore it recommends using the following standard functionality.

</details>

-----

<details>
<summary>Stakeholders</summary>

- Mrs. Nutsy - CEO
- Mr. Grey Bear - top performing agent

</details>

<details>
<summary>Standard Objects</summary>

- **Users** - are separate real estate agents
- **Account** - real estate business companies
- **Contact** - customers who want to buy/rent properties
- **Opportunity** - will help you associate your `Customers` with `Properties`. `Opportunity` Custom Fields:
  - Lookup: **Property**
- Other standard objects can also be used

</details>

<details>
<summary>Custom Objects</summary>

- Property (Record Types: **Rent**, **Sale**)

  - Lookup: **Account** - <span style="color:#F94C66"><span style="color:#F94C66">required</span></span>
  - Text(255): **Property Title**
  - Number(16, 2): **Price**
  - Text(255): **Address**
  - Text Area (Long)(1000): **Description**
  - TextArea(Rich)(1000): **Property Image**
  - Date: **Available From**
  - Date: **Available Due**

- Payment
  - Lookup: **Property** - <span style="color:#F94C66"><span style="color:#F94C66">required</span></span>
  - Formula Field: **Property Price**
  - Formula(Percent): **Real Estate Fee** (if Property is being _sold_ = 10% of Price, if Property is being _rented_ = 50% of Price)
  - Formula(Number): **Total Payment** (price and fee)
  - Picklist: **Status** (Payed, Prepared, Declined, Pending)
  - Lookup: **User** - <span style="color:#F94C66">required</span>
  - Lookup: **Contact** - <span style="color:#F94C66">required</span>

</details>

---

<details>
<summary>Business Requirements</summary>

- ***Property Information*** <br>
Mrs. Nutsy wants a way to store relevant information about the properties. She currently doesn’t have time to specify all the information they gather about the properties, so she relies on your knowledge of real estate business. As a final note she added that their business supports both renting and selling of properties, so she’d be happy to have customized UI based on the type.
- ***Tracking the progress*** <br>
Mr. Grey Bear also asking for an ability to track the progress of negotiations with potential Customers and thinks that Opportunity Path can be customized to suit his needs
Mrs. Nutsy has great confidence in your ability to deliver a great solution and therefore she provided some reference pictures which would help to ignite your imagination in data modeling. Also think about information that might be useful for customers.

</details>

---

<h2 style="text-align:center">Walk-through</h2>

1. Create custom Objects: `Property`, `Payment`.

<img src="./Images/prop_payment.png">

2. (optional) Create *custom* App.
3. (optional) Create tabs for `Property` and `Payment` objects add them to the App.

<img src="./Images/prop_payment_tabs.png"><br>
<img src="./Images/prop_payment_tabs(1).png">

4. Create 2 *record* types for `Property` Object: `Rent`, `Sale`.

<img src="./Images/rent_sale_rec_type_for_prop_obj.png"> <br>
<img src="./Images/rent_sale_rec_type_for_prop_obj(1).png">

5. Create fields for `Property` and `Payment` objects.

<img src="./Images/prop_payment_fields.png">

6. Create Validation rules:
   - Price cannot be less than Zero
   - Price cannot be empty
   - Available Due cannot be before Available From
  
<img src="./Images/prop_validation_rules.png">

7. Create two page layouts for Property: `Rent`, `Sale`.

<img src="./Images/Prop_Page_layout_list.png">

8. For created record types, specify the fields which suit more for the specific record type. Assign the correct page layouts to record types.

<img src="./Images/Page_layout_assign_by_record_type.png">

9. Create fields for the Opportunity standard object.

<img src="./Images/Custom_field_for_opportunity.png">

10. Create 4 Property records with pictures (see pictures attached below in the document)

<img src="./Images/Magic_property1.png"> <br>
<img src="./Images/Magic_property2.png"> <br>
<img src="./Images/Magic_property3.png"> <br>
<img src="./Images/Magic_property4.png"> <br>

11. Create Sample records for each created object and created field.

<img src="./Images/Payment_record.png"> <br>
<img src="./Images/Opportunity_with_a_magic_house.png"> <br>
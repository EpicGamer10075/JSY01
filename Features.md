1. Add Request behavior
- From the Customer View:
  - When “Add Request” is clicked, the request pane should open.
  - The cursor should automatically move to the Title field.
  - All existing text in the Title field should automatically be highlighted.
- From the Title View:
  - When “Add Request” is clicked, the request pane should open.
  - The cursor should automatically move to the Customer field, which is the current default.
  - All existing text in the Customer field should automatically be highlighted.
The Customer field should also automatically suggest matching customer names as the user types. The match should work as long as the customer's name contains the typed string. Essentially, we should take the existing search/autocomplete functionality used for Title selection and add similar functionality to Customer selection.
I think we can handle the Add Request behavior by tracking which tab is currently selected and passing that information into the function that opens the pane:
- If the Customer tab is selected → focus/highlight Title.
- If the Title tab is selected → focus/highlight Customer.

2. Undo button
The project sponsor wants an Undo button located near the Edit/View mode buttons.
He only requested the ability to undo the most recent action, so we should not need to build a full undo history. We will likely just need to temporarily store the last action and provide a way to reverse it.

3. Add Tag Request button
The project sponsor wants us to investigate what the existing “Add Tag Request” button actually does.

4. Edit Mode login improvements
When logging into Edit Mode:
- The application should notify the user if Caps Lock is enabled.
- If the login fails, a popup should explain why. In most cases, this will probably just say something along the lines of “Password was incorrect.”

5. Main search bar
The project sponsor wants a double-click inside the main search bar to clear the current search/results.

6. Historical customer and title data
The project sponsor wants the application to begin preserving historical request data.
For each customer, we should retain:
- Previous title requests.
- The date of each request.
For each title, we should retain:
- Previous customers who requested it.
- The date of those requests.
- The number of times the title has been requested over time.
This will probably require some database changes, so we should discuss the best way to structure the historical data before implementing it.
7. Flag toggle in View Mode
The Flag toggle should be disabled while the application is in View Mode.
Ideally:
- It should not be clickable.
- It should also appear grayed out or otherwise visually disabled.
8. New Customer fields
Two new fields need to be added to the Customer data:
- Creation Date — automatically populated whenever a new customer is created.
- Last Flagged Date — stores the most recent date that customer was flagged.

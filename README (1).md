# Staff Purchase Requisition Management System

A simple, console-based Python application for submitting and managing
staff purchase requisitions.

The application is contained in **one Python file** and uses Python's
standard library. It does not require a graphical interface or
third-party packages.

## Features

-   Enter staff details and requisition dates.
-   Add one or more purchase items to a requisition.
-   Calculate the total cost of all items.
-   Generate sequential requisition IDs starting from `10001`.
-   Automatically approve requisitions with a total **below \$500.00**.
-   Keep requisitions with a total of **\$500.00 or more** pending for a
    manager's decision.
-   Allow a manager to approve or reject pending requisitions.
-   Generate an approval reference using the staff ID and the final
    three digits of the requisition ID.
-   Display all requisition records.
-   Display statistics for total submitted, approved, pending and not
    approved requisitions.
-   Validate required text, dates and monetary amounts.

## Requirements

-   Python 3.9 or later
-   No third-party packages are required.

The program uses Python standard-library modules, including `datetime`
and `decimal`.

## How to Run

1.  Download or clone this repository.
2.  Open the project folder in a terminal or Visual Studio Code.
3.  Run the following command:

``` bash
python Staff_Purchase_Requisition_System.py
```

On some systems, use:

``` bash
python3 Staff_Purchase_Requisition_System.py
```

## How to Use

When the program starts, a menu appears:

``` text
STAFF PURCHASE REQUISITION SYSTEM
1. Submit a requisition
2. Manager response
3. Display all requisitions
4. Display statistics
5. Exit
```

Choose an option by entering its number.

### 1. Submit a requisition

Enter: - Date in `DD/MM/YYYY` format - Staff ID - Staff name - Item name
and item cost

You can add multiple items to the same requisition. The system
calculates the total and applies the approval rule.

### 2. Manager response

The system displays pending requisitions. Enter the requisition ID, the
decision (`Approved` or `Not approved`) and the manager's name.

Only requisitions with `Pending` status can receive a manager decision.

### 3. Display all requisitions

Displays each stored requisition, including staff details, items, total,
status, approval reference and decision maker.

### 4. Display statistics

Displays: - Total submitted - Approved - Pending - Not approved

### 5. Exit

Closes the program.

## Approval Rule

  -----------------------------------------------------------------------
  Requisition total       Initial status          Next step
  ----------------------- ----------------------- -----------------------
  Below \$500.00          Approved                Approval reference is
                                                  generated automatically

  Exactly \$500.00        Pending                 Manager decision
                                                  required

  Above \$500.00          Pending                 Manager decision
                                                  required
  -----------------------------------------------------------------------

The comparison is strictly **less than \$500.00**. Therefore, a total of
exactly \$500.00 is not automatically approved.

## Requisition ID and Approval Reference

-   The first requisition ID is `10001`.
-   Each new requisition increases the ID by one.
-   The approval reference combines the staff ID with the final three
    digits of the requisition ID.
-   A reference is issued for approved requisitions. Pending and
    rejected requisitions display `Not issued`.

## Code Structure

The project is intentionally kept in one file to make it straightforward
to open, run and study.

  -----------------------------------------------------------------------
  Component                           Responsibility
  ----------------------------------- -----------------------------------
  Settings/constants                  Stores the approval limit, starting
                                      ID and status labels

  Input-check functions               Validates text, dates and prices

  `Requisition` class                 Stores one request, its items,
                                      total and approval decision

  `RequisitionSystem` class           Creates, searches and manages all
                                      requests and calculates statistics

  Console functions                   Collect user input and display
                                      results

  `run_program()`                     Runs the menu loop and handles
                                      input errors
  -----------------------------------------------------------------------

## Data and Limitations

-   Requisition records are stored in memory while the program is
    running.
-   Records are **not saved permanently**. They are lost when the
    program closes.
-   The application does not include a database, user login, role-based
    access or a graphical interface.
-   The manager response feature demonstrates the approval workflow; it
    does not authenticate a real manager.
-   This is an educational console application and should not be treated
    as a production financial system.

## Example Workflow

1.  Submit a requisition with a total of `$120.00`.
2.  The system automatically marks it as `Approved`.
3.  Submit another requisition with a total of `$650.00`.
4.  The system marks it as `Pending`.
5.  Choose **Manager response** and approve or reject that pending
    request.
6.  Display all requisitions and statistics to see the updated status.

## Author

**Student:** \Rudransh\

------------------------------------------------------------------------

This project was developed for learning and assessment purposes.

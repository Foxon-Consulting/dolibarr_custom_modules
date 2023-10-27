# PROPOSALWITHDAYS FOR [DOLIBARR ERP CRM](https://www.dolibarr.org)

## Features

Calculate the price for proposals/invoices lines using a second argument `days` along with the quantity

The total price of the line (Qty * Unit price) is then multiplicated by the number of `days`


## Prerequisites

The "Proposals" module must be activated (work also with the "Invoices" module)

The "days" parameter must be configured in the proposal module (and "Invoices" if needed) under "Complementary attributes (lines)" with these mandatory parameters:
- Label: Days
- Attribute code: days
- Type: Float (can also be integer if only full days)
- Visibility: 0


## Installation

### Manually
- Make sure Dolibarr is already installed and configured
- Copy the module under htdocs/custom/ in your server

### Final steps
From your browser:

- Log into Dolibarr as a super-administrator
- Go to "Setup" -> "Modules"
- You should now be able to find and enable the module (make sure you also have the "Proposals" module activated)


## Documentation

The operations are done in the `interface_99_modProposalWithDays_ProposalWithDaysTriggers.class.php` file, in the runTrigger method

There are also 4 files under the core/tpl directory that override the base templates of the Proposals interface:
 - `objectline_title.tpl.php`: The table header, modified to include a column "Days"
 - `objectline_view.tpl.php`: The table content (called in a loop of lines), same thing, we add a column displaying the `days`
 - `objectline_create.tpl.php`: Displayed under the table, it's the part creating a new line, we add an input here for the `days`
 - `objectline_edit.tpl.php`: When editing a line, also adds an input to edit the `days`value

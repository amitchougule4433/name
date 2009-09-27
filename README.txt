/* $Id$ */

-- SUMMARY --

Name is a module that provides a number of name fields and a FAPI name element.

Each field is summaried below: 

1) Name: 'Mr' 'John Doe' 
2) Name: 'John' 'Doe'
3) Name: 'Mr' 'John' 'Doe'
4) Name: 'Mr' 'John' 'A.' 'Doe'
5) Name: 'Mr' 'John' 'A.' 'Doe', 'PhD'

Each field is made up for two or more input fields. The title field is a select
list and the other fields are all text fields.

Multiple values are supported via the core fields engine.

-- REQUIREMENTS --

* None.

You will require the Field UI module to add fields to content.

-- INSTALLATION --

* Standard installation, see http://drupal.org/node/70151 for further information.

-- UPGRADING --

* N/A - This is a new module.

-- RELATED MODULES --

* Fullname field for CCK
  A similar module for Drupal 5 CCK, but with support for two concurrent name
  field sets for each entry. A legal and preferred set of:
  
  prefix, firstname, middlename, lastname, and suffix
   
  http://drupal.org/project/cck_fullname
  
* Namefield
  An "experiment" Drupal 5 development module.

  http://drupal.org/project/namefield

-- CONFIGURATION --

* There are no special configuration requirements. Just add these like any
  other Drupal fields.

-- DETAILS --

The following is a more in depth summary of the five fields.

Key:

[-- \/] A select element
[     ] A textfield

1) Name: Mr "John Doe" 

Input:              [-- \/] [     ]
Description:        This field stores a users title and name.
Database fields:    'title', 'name'

2) Name: John Doe

Input:              [     ] [     ]
Description:        This field stores a users first and last name.
Database fields:    'firstname', 'lastname'

3) Name: Mr John Doe

Input:              [-- \/] [     ] [     ]
Description:        This field stores a users title, first and last names.
Database fields:    'title', 'firstname', 'lastname'

4) Name: Mr John A. Doe

Input:              [-- \/] [     ] [     ] [     ]
Description:        This field stores a users title, first, middle and last names.
Database fields:    'title', 'firstname', 'middlename', 'lastname'

5) Name: Mr John A. Doe, PhD

Input:              [-- \/] [     ] [     ] [     ]
                    [                           ]
Description:        This field stores a users title, credentials, first, middle and last names.
Database fields:    'title', 'firstname', 'middlename', 'lastname', 'credentials'

For a full description visit the project page:
  http://drupal.org/project/name
Bug reports, feature suggestions and latest developments:
  http://drupal.org/project/issues/name

-- THEMING --

Two global theming functions are available. These can be
used on all name fields. The <code>$element['#item']['safe_' . $KEY]</code>
has been passed through the <code>check_plain</code> function.

The <code>$element['#item']</code> values and their corresponding safe
values are called keyed by their database field names. You must use isset()
as many fields may not be set.
 
/**
 * Theme function available for the all name fields.
 * Display name: Name(s)
 */
function THEME_field_formatter_name_short($element) {
  return theme_field_formatter_name_short($element);
}

/**
 * Theme function available for the all name fields.
 * Display name: Title name(s)
 */
function THEME_field_formatter_name_default($element) {
  return theme_field_formatter_name_default($element);
}

/**
 * Theme function available for the extended name field.
 * Fields: "'Mr' 'John' 'A.' 'Doe', 'PhD'" only
 * Display name: Title name(s), credentials
 */
function theme_field_formatter_name_complete($element) {
  return theme_field_formatter_name_complete($element);
}

-- REFERENCES --

For details about Drupal 7 Fields API:
  http://drupal.org/node/443536
For details about Drupal 7 FAPI:
  http://api.drupal.org/api/drupal/developer--topics--forms_api.html/7
  http://api.drupal.org/api/drupal/developer--topics--forms_api_reference.html/7
  
-- CONTACT --

Current maintainers:

* Alan D. - http://drupal.org/user/54136

If you want to help or be involved please contact me.

If you find any issues please lodge an issue after checking that the issue
is not a duplicate of an existing issue.
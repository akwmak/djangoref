# Django Cheat Sheet

The goal of this in-progress repository will be to concisely capture / document common, core Django tools. Where appropriate, code samples will be added to highlight common use cases.

## Contents

#### Templates
- Tags
- Filters
- Date formats

#### Models

- Common field options (kwargs)
  - null
  - blank
  - choices
  - db_column
  - db_index
  - default
  - editable
  - error_messages
  - help_text
  - primary_key
  - unique
  - unique_for_date
  - unique_for_month
  - unique_for_year
  - verbose_name
  - validators
- Fields
  - Numbers
  - Boolean
  - Strings
  - Dates & Times
  - Internet
  - Files
  - Relationships
- `Meta` attributes
  - abstract
  - app_label
  - db_table
  - get_latest_by
  - managed
  - ordering
  - permissions
  - proxy
  - unique_together
  - index_together
  - verbose_name
  - verbose_name_plural
- Validators

#### Signals (NOTE: Perhaps nest these under their appropriate sections)

- django.db.models.signals
- django.core.signals
- etc.

#### Querysets

- Methods
  - all()
  - none()
  - <code>filter(*query*)</code>
  - <code>exclude(*query*)</code>
  - `order_by(field...)`
  - etc.
- Queries (lookups)
  - exact
  - iexact
  - contains
  - gt
  - etc.
- Aggregation functions

#### Forms

- Common kwargs
  - required
  - label
  - help_text
  - initial
  - validators
  - widget
  - error_messages
  - localize
- Fields
  - Boolean
  - Strings
  - Choices
  - Dates & Times
  - Numbers
  - Files
  - Internet
  - Misc
- Validators
- Views
  - Shortcuts
  - Decorators
  - GCBV
- Formsets
- Widgets
- ModelForm & ModelFormSet

#### Admin

- ModelAdmin
  - Options and callbacks
- InlineModelAdmin
- AdminSite

#### Settings
#### Testing
#### Urls
#### Management commands

  - Migrations
  - Shell
  - Server
  - etc.

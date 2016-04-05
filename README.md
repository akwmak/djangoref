# Django Cheat Sheet

The goal of this in-progress repository will be to concisely capture / document common, core Django tools. Where appropriate, code samples will be added to highlight common use cases. Links to popular Stack Overflow answers will also be added to further explain topics.

## Contents

#### Templates
- Tags
- Filters
- Date formats

#### [Models](#model-section)

- [Field options (kwargs)](#model-fields)
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

#### Misc (not sure if these are staying)
- The `request` object
- [Custom user models](http://stackoverflow.com/questions/44109/extending-the-user-model-with-custom-fields-in-django)
- [File upload example](http://stackoverflow.com/a/8542030/3518452)
- `null` vs. `blank` &mdash; Differences, and when to use them


## <a name="model-section"></a>Models

### <a name="model-fields"></a>Field Options

| option           | type                     | default |
|------------------|--------------------------|---------|
| null             | boolean                  | False |
| blank            | boolean                  | False |
| choices          | iterable (list or tuple) | None |
| db_column        | string | None |
| db_index         | boolean | False |
| db_tablespace    | string | None |
| default          | value or callable | [NOT_PROVIDED](https://docs.djangoproject.com/en/dev/_modules/django/db/models/fields/) |
| editable         | boolean | True |
| error_messages   | dictionary | None |
| help_text        | string | `''` (empty string) |
| primary_key      | boolean | False |
| unique | boolean | False |
| unique_for_date  | string (`DateField` or `DateTimeField` name) | None |
| unique_for_month | string (`DateField` or `DateTimeField` name) | None |
| unique_for_year  | string (`DateField` or `DateTimeField` name) | None |
| verbose_name     | string | None |
| validators       | list | `[]` (empty list) |

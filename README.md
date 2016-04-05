# Django Cheat Sheet

The goal of this in-progress repository will be to concisely capture / document common, core Django tools. Where appropriate, code samples will be added to highlight common use cases. Links to popular Stack Overflow answers will also be added to further explain topics.

## Contents

#### Templates
- Tags
- Filters
- Date formats

#### [Models](#model-section)

- [Field options (kwargs)](#model-field-options)
- [Fields](#model-fields)
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

### <a name="model-field-options"></a>Field Options

| Option           | Type                     | Default |
|------------------|--------------------------|---------|
| `null`             | boolean                  | `False` |
| `blank`            | boolean                  | `False` |
| `choices`          | iterable (list or tuple) | `None` |
| `db_column`        | string | `None` |
| `db_index`         | boolean | `False` |
| `db_tablespace`    | string | `None` |
| `default`          | value or callable | [`NOT_PROVIDED`](https://docs.djangoproject.com/en/dev/_modules/django/db/models/fields/) |
| `editable`         | boolean | `True` |
| `error_messages`   | dictionary | `None` |
| `help_text`        | string | `''` (empty string) |
| `primary_key`      | boolean | `False` |
| `unique` | boolean | `False` |
| `unique_for_date`  | string (`DateField` or `DateTimeField` name) | `None` |
| `unique_for_month` | string (`DateField` or `DateTimeField` name) | `None` |
| `unique_for_year`  | string (`DateField` or `DateTimeField` name) | `None` |
| `verbose_name`     | string | `None` |
| `validators`       | list | `[]` (empty list) |

### <a name="model-fields"></a>Fields

| Field Name | Options | Notes |
|------------|------------------|----------|-|-|
| `AutoField` | | You usually won’t need to use this directly. |
| `BigIntegerField` | | For integers between -9223372036854775808 and 9223372036854775807 |
| `BinaryField` | | Reminder: don't store files in the db |
| `BooleanField` | | A true / false field. Use `NullBooleanField` to accept `NULL` values |
| `CharField` | <code>max_length=<em>None</em></code> | For small- to medium-sized strings |
| `CommaSeparatedIntegerField` | <code>max_length=<em>None</em></code> | |
| `DateField` | [<code>auto_now=<em>False</em></code>] <br> [<code>auto_now_add=<em>False</em></code>] | |
| `DateTimeField` | [<code>auto_now=<em>False</em></code>] <br> [<code>auto_now_add=<em>False</em></code>] | |
| `DecimalField` | <code>max_digits=<em>None</em></code> <br> <code>decimal_places=<em>None</em></code> | Uses Python's `Decimal` type |
| `DurationField` | | Modeled in Python by `timedelta` |
| `EmailField` | [<code>max_length=<em>254</em></code>] | Uses `EmailValidator` to validate input |
| `FileField` | [<code>upload_to=<em>None</em></code>] <br> [<code>max_length=<em>100</em></code>] | |
| `FilePathField` | <code>path=<em>None</em></code> <br> [<code>match=<em>None</em></code>] <br> [<code>recursive=<em>False</em></code>] <br> [<code>max_length=<em>100</em></code>] | |
| `FloatField` | | Uses Python's `float` type |
| `GenericIPAddressField` | [<code>protocol=<em>'both'</em></code>] <br> [<code>unpack_ipv4=<em>False</em></code>] | If `blank=True`, `null` must be `True` |
| `ImageField` | [<code>upload_to=<em>None</em></code>] <br> [<code>height_field=<em>None</em></code>] <br> [<code>width_field=<em>None</em></code>] <br> [<code>max_length=<em>100</em></code>] | Requires the [Pillow](https://pillow.readthedocs.org/en/latest/) library |
| `IntegerField` | | For integers between -2147483648 and 2147483647 |
| `NullBooleanField` | | Like `BooleanField`, but allows `NULL` values by default |
| `PositiveIntegerField` | | Like an `IntegerField`, but must be either positive or zero (0). |
| `PositiveSmallIntegerField` | | A `PositiveIntegerField` for small values. Values from 0 to 32767 are safe in all databases. |

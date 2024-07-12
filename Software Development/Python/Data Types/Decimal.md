# Dealing with additional zeroes after the decimal in python's Decimal objects.
> [!info] References
> - Google: `python string to decimal creates leading decimal zeroes`
> - https://stackoverflow.com/questions/11227620/drop-trailing-zeros-from-decimal
> - https://docs.python.org/3/library/decimal.html#decimal-faq

>[!info] Tip
>In Django, the DecimalField has a `context` property which stores the precision (django's `max_digits`), but not the allowed decimal places (django's `decimal_places`). So what I do when dealing with creating `Decimal` objects from `float` is:
>```py
>if type(field) == DecimalField:
>	value = field.context.create_decimal_from_float(value).normalize()
> ```




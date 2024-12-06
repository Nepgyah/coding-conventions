## Class Naming Conventions
No need to suffix view/form/serializer classes with View/Form/Serializer
```
/* Bad */
class SetPassword(generic.FormView):
    form_class = forms.NewPassword

/* Good */
class SetPassword(generic.FormView):
    form_class = forms.NewPasswordForm
    
```

# Model Field Naming Conventions
`DateTimeField`s should generally have suffix `_at`. For example:

- `created_at`
- `sent_at`
- `period_starts_at`

There are some exceptions such as `available_from` and `available_to` but stick with the convention unless you have a very good reason not to.

`DateField`s should have suffix `_date`:

- `billing_date`
- `supply_date`

This convention also applies to variable names.

## Model Method Naming Convetions
- For query methods (i.e. methods that look something up and return it), prefix with `get_`.
    
- For setter methods (i.e. methods that set fields and call save), prefix with `set_`.
    
- Prefer "latest" to "last" in method names as "latest" implies chronological order where the ordering is not explicit when using "last"; i.e. `get_latest_payment_schedule`. Similarly, prefer `earliest` to `first` in method names.
## Encapsulate Model Mutation
Don't call a model's `save` method from anywhere but "mutator" methods on the model itself.

Similarly, avoid calling `SomeModel.objects.create` or even `SomeModel.related_objects.create` from outside of the model itself. Encapsulate these in "factory" methods (classmethods for the `objects.create` call).

Doing this provides a useful overview of the lifecycle of a model as you can see all the ways it can mutate in one place.

Also, this practice leads to better tests as you have a simple, readable method to stub when testing units that call into the model layer.

## Group Methods and Properties on models
To keep models well organised and easy to understand, group their methods and properties into these groups using a comment:

- Factories
- Mutators
- Queries
- Properties

```
class SomeModel(models.Model):
    name = models.CharField(max_length=255)

    # Factories

    @classmethod
    def new(cls, name):
        return cls.objects.create(name=name)

    # Mutators

    def anonymise(self):
        self.name = ""
        self.save()

    def set_name(self, new_name):
        self.name = new_name
        self.save()

    # Queries

    def get_num_apples(self):
        return self.fruits.filter(type="APPLE").count()

    # Properties

    @property
    def is_called_dave(self):
        return self.name.lower() == "dave"
```
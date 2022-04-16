# Forms

## The form object

| Attribute  | Type           | Description                                                                          |
| ---------- | -------------- | ------------------------------------------------------------------------------------ |
| id         | `string`       | A unique identifier.                                                                 |
| formTitle  | `string`       | The forms's title, meant to be displayable to the users.                             |
| formFields | `form field[]` | An array of [form fields](#form-field).                                              |
| createdAt  | `timestamp`    | Time at which the object was created. Measured in seconds since the Unix epoch.      |
| updatedAt  | `timestamp`    | Time at which the object was last updated. Measured in seconds since the Unix epoch. |

## The form field object

| Attribute    | Type                                           | Description                                                                          |
| ------------ | ---------------------------------------------- | ------------------------------------------------------------------------------------ |
| id           | `string`                                       | A unique identifier.                                                                 |
| label        | `string`                                       |                                                                                      |
| descriptions | `string`                                       |                                                                                      |
| defaultValue | `string`                                       |                                                                                      |
| required     | `boolean`                                      |                                                                                      |
| rowIndex     | `number`                                       |                                                                                      |
| component    | `string`                                       |                                                                                      |
| options      | `{id: string; label: string; value: string}[]` |                                                                                      |
| editable     | `boolean`                                      |                                                                                      |
| deletable    | `boolean`                                      |                                                                                      |
| props        | `{[key: string]: any};`                        |                                                                                      |
| createdAt    | `timestamp`                                    | Time at which the object was created. Measured in seconds since the Unix epoch.      |
| updatedAt    | `timestamp`                                    | Time at which the object was last updated. Measured in seconds since the Unix epoch. |

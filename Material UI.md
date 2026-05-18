### Components:
#### Most important components to learn first:
|Learn first|Components|
|---|---|
|Layout|`Box`, `Stack`, `Grid`, `Container`|
|Text|`Typography`|
|Actions|`Button`, `IconButton`|
|Forms|`TextField`, `Checkbox`, `Radio`, `Select`, `MenuItem`, `FormControl`|
|Display|`Card`, `CardContent`, `Avatar`, `Chip`, `Divider`|
|Feedback|`Alert`, `Snackbar`, `Dialog`, `CircularProgress`|
|Navigation|`AppBar`, `Toolbar`, `Drawer`, `Menu`, `Tabs`|

#### Components:
|Component|Used / Description|Where it cannot / should not be used|Example|
|---|---|---|---|
|`Box`|General-purpose wrapper for layout and styling. Best replacement for a styled `<div>`.|Should not be used when a more semantic component is better, like `Button`, `Typography`, or `Card`.|`<Box sx={{ p: 2 }}>Content</Box>`|
|`Typography`|Used for text such as headings, paragraphs, subtitles, and captions.|Should not be used for clickable actions. Use `Button` or `Link` instead.|`<Typography variant="h5">Dashboard</Typography>`|
|`Button`|Used for actions like submit, save, delete, login, etc.|Should not be used for navigation links unless styled intentionally. Use `Link` for normal navigation.|`<Button variant="contained">Save</Button>`|
|`IconButton`|Used when the button contains only an icon, like delete, menu, close, or edit.|Should not be used for text buttons. Use `Button` instead.|`<IconButton><DeleteIcon /></IconButton>`|
|`TextField`|Used for user input like name, email, password, phone number, etc.|Should not be used for non-editable display text. Use `Typography` instead.|`<TextField label="Email" />`|
|`Checkbox`|Used when the user can select multiple options or turn something on/off.|Should not be used when only one option can be selected from a group. Use `Radio` instead.|`<Checkbox checked={agree} />`|
|`Radio`|Used when the user must select only one option from a group.|Should not be used for multiple selections. Use `Checkbox` instead.|`<Radio value="male" />`|
|`Select`|Used for dropdown selection from a list of options.|Should not be used for long searchable lists. Use `Autocomplete` instead.|`<Select value={age}>...</Select>`|
|`MenuItem`|Used inside `Select`, `Menu`, or dropdown lists.|Should not usually be used alone outside menu/select components.|`<MenuItem value={10}>Ten</MenuItem>`|
|`FormControl`|Wraps form elements like `Select`, `RadioGroup`, and input labels. Helps manage form state.|Not needed for simple `TextField` in many cases because `TextField` already includes form control behavior.|`<FormControl fullWidth>...</FormControl>`|
|`InputLabel`|Adds a label for input components, especially `Select`.|Usually not needed with `TextField` because `TextField` has a `label` prop.|`<InputLabel>Age</InputLabel>`|
|`Stack`|Used for simple vertical or horizontal spacing between components.|Should not be used for complex responsive layouts. Use `Grid` instead.|`<Stack spacing={2}>...</Stack>`|
|`Grid`|Used for responsive page layouts with rows and columns.|Should not be used just to add small spacing between two items. Use `Stack` instead.|`<Grid container spacing={2}>...</Grid>`|
|`Container`|Centers content and limits page width. Common for pages and sections.|Should not be used inside every small component. Usually used near the page level.|`<Container maxWidth="md">...</Container>`|
|`Card`|Used to display grouped content, such as product cards, profile cards, or dashboard widgets.|Should not be used for full-page layout. Use `Box`, `Container`, or `Grid`.|`<Card>...</Card>`|
|`CardContent`|Used inside `Card` to hold text and content.|Should not usually be used outside a `Card`.|`<CardContent>Profile info</CardContent>`|
|`CardActions`|Used inside `Card` for buttons/actions.|Should not be used outside a `Card`.|`<CardActions><Button>View</Button></CardActions>`|
|`Avatar`|Used to show user images, initials, or profile icons.|Should not be used for large images or banners. Use normal image elements or MUI media components.|`<Avatar>SR</Avatar>`|
|`Chip`|Used for small labels, tags, filters, or status indicators.|Should not be used for long text or paragraphs.|`<Chip label="Active" color="success" />`|
|`Divider`|Used to visually separate content.|Should not be overused for spacing. Use margin/padding with `sx` instead.|`<Divider />`|
|`Alert`|Shows important messages like success, error, warning, or info.|Should not be used for normal text content. Use `Typography`.|`<Alert severity="success">Saved!</Alert>`|
|`Snackbar`|Shows temporary popup messages, usually after an action.|Should not be used for permanent messages. Use `Alert` or page content instead.|`<Snackbar open={open} message="Saved" />`|
|`Dialog`|Used for modal popups that require user attention, confirmation, or input.|Should not be used for simple notifications. Use `Snackbar` or `Alert`.|`<Dialog open={open}>...</Dialog>`|
|`CircularProgress`|Shows loading state using a spinner.|Should not be shown when nothing is loading.|`<CircularProgress />`|
|`LinearProgress`|Shows loading progress as a horizontal bar.|Should not be used for small inline loading icons. Use `CircularProgress`.|`<LinearProgress />`|
|`AppBar`|Used for top navigation/header bars.|Should not be used inside small cards or forms.|`<AppBar position="static">...</AppBar>`|
|`Toolbar`|Used inside `AppBar` to align navigation items.|Usually not needed outside app/header layouts.|`<Toolbar>...</Toolbar>`|
|`Drawer`|Used for side navigation panels.|Should not be used for small popup menus. Use `Menu` instead.|`<Drawer open={open}>...</Drawer>`|
|`Menu`|Used for dropdown action menus.|Should not be used for large navigation sidebars. Use `Drawer`.|`<Menu open={open}>...</Menu>`|
|`Tabs`|Used to switch between related views on the same page.|Should not be used for unrelated navigation. Use normal routing/navigation.|`<Tabs value={tab}>...</Tabs>`|
|`Tab`|Individual tab inside `Tabs`.|Should not be used alone without `Tabs`.|`<Tab label="Profile" />`|
|`Autocomplete`|Used for searchable dropdowns or suggestions.|Not needed for very small option lists. Use `Select`.|`<Autocomplete options={users} renderInput={(params) => <TextField {...params} label="User" />} />`|
|`Tooltip`|Shows small helper text on hover/focus.|Should not contain important information that users must always see.|`<Tooltip title="Delete"><IconButton>...</IconButton></Tooltip>`|
|`Badge`|Shows small counts or status indicators, often on icons.|Should not be used for large labels or detailed messages. Use `Chip` or `Alert`.|`<Badge badgeContent={4} color="error">...</Badge>`|
|`Paper`|Surface component with background and elevation. Used for panels or sections.|Should not be used for every wrapper. Use `Box` for simple layout.|`<Paper elevation={3}>Content</Paper>`|
|`Link`|Used for navigation or external links.|Should not be used for submitting forms or actions. Use `Button`.|`<Link href="/about">About</Link>`|

#### Small Example:
```JavaScript
import {
  Alert,
  Box,
  Button,
  Card,
  CardContent,
  Container,
  Stack,
  TextField,
  Typography,
} from "@mui/material";

function ProfileForm() {
  return (
    <Container maxWidth="sm">
      <Box sx={{ mt: 4 }}>
        <Card>
          <CardContent>
            <Stack spacing={2}>
              <Typography variant="h5">
                Create Profile
              </Typography>

              <Alert severity="info">
                Please fill all required fields.
              </Alert>

              <TextField label="Name" fullWidth />
              <TextField label="Email" fullWidth />

              <Button variant="contained">
                Submit
              </Button>
            </Stack>
          </CardContent>
        </Card>
      </Box>
    </Container>
  );
}
```


----
### Property:
#### Most important props to learn first:
| Priority  | Props                                                                             |
| --------- | --------------------------------------------------------------------------------- |
| Must know | `variant`, `color`, `size`, `sx`, `disabled`, `fullWidth`                         |
| Forms     | `label`, `value`, `onChange`, `error`, `helperText`, `required`, `type`           |
| Layout    | `spacing`, `direction`, `sx`, `container`, `size`, `alignItems`, `justifyContent` |

#### Properties:

| Property                 | Used / Description                                                                                                                              | Where it cannot be used                                                                                                                 | Example                                                             |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `variant`                | Changes the visual style of a component. Common in `Button`, `TextField`, `Typography`, `Alert`, etc.                                           | Cannot be used on plain HTML tags like `<div>` unless wrapped with MUI styling. Not all MUI components support the same variant values. | `<Button variant="contained">Save</Button>`                         |
| `color`                  | Applies theme color such as `primary`, `secondary`, `error`, `success`, `warning`, or `info`.                                                   | Not all components support `color`. For example, layout components like `Box` usually use `sx` instead.                                 | `<Button color="error">Delete</Button>`                             |
| `size`                   | Changes component size, commonly `small`, `medium`, or `large`.                                                                                 | Not useful on layout-only components like `Box`. Some components may support only limited size values.                                  | `<Button size="large">Submit</Button>`                              |
| `sx`                     | Adds custom CSS and theme-aware styling directly to MUI components. Very important for spacing, layout, colors, borders, and responsive styles. | Usually not available on normal HTML elements like `<div>` unless using MUI’s `Box`, `styled`, or MUI components.                       | `<Box sx={{ p: 2, mt: 3 }}>Hello</Box>`                             |
| `disabled`               | Disables user interaction. Common on `Button`, `TextField`, `Checkbox`, `Radio`, `Select`.                                                      | Not meaningful on display-only components like `Typography`, `Card`, or `Box`.                                                          | `<Button disabled>Submit</Button>`                                  |
| `fullWidth`              | Makes the component take the full width of its parent container. Common on `Button` and `TextField`.                                            | Not available on every component. For layout components, use `sx={{ width: "100%" }}` instead.                                          | `<TextField fullWidth label="Email" />`                             |
| `label`                  | Displays a label for input fields. Mostly used with `TextField`, `Select`, `InputLabel`, etc.                                                   | Not used on `Button`, `Box`, `Typography`, `Card`, or `Stack`.                                                                          | `<TextField label="Username" />`                                    |
| `value`                  | Stores the current value of an input component. Used in controlled forms.                                                                       | Not used for layout or display components like `Box`, `Stack`, `Card`, or `Typography`.                                                 | `<TextField value={name} />`                                        |
| `onChange`               | Runs a function when the input value changes. Important for forms.                                                                              | Not useful on static display components unless they are interactive.                                                                    | `<TextField onChange={(e) => setName(e.target.value)} />`           |
| `onClick`                | Runs a function when the user clicks the component. Common on `Button`, `IconButton`, `CardActionArea`, etc.                                    | Can technically be added to many components, but should not be used for non-clickable UI unless accessibility is handled.               | `<Button onClick={handleSave}>Save</Button>`                        |
| `error`                  | Shows an error state, usually red styling. Common with `TextField`, `FormControl`, etc.                                                         | Not used on normal layout components like `Box`, `Grid`, or `Stack`.                                                                    | `<TextField error label="Email" />`                                 |
| `helperText`             | Shows extra helper or validation text below a `TextField`.                                                                                      | Mainly for `TextField`. Not used on `Button`, `Box`, `Typography`, etc.                                                                 | `<TextField helperText="Enter a valid email" />`                    |
| `required`               | Marks a form field as required.                                                                                                                 | Not useful on non-form components.                                                                                                      | `<TextField required label="Email" />`                              |
| `type`                   | Sets input type such as `text`, `password`, `email`, or `number`.                                                                               | Mostly used with input components like `TextField`. Not used on `Button`, `Box`, `Card`, etc.                                           | `<TextField type="password" label="Password" />`                    |
| `placeholder`            | Shows temporary hint text inside an input.                                                                                                      | Used mainly with input components. Not used on display/layout components.                                                               | `<TextField placeholder="Enter your name" />`                       |
| `spacing`                | Adds space between children. Very common with `Stack` and `Grid container`.                                                                     | Not used on `Button`, `TextField`, or `Typography`. For `Box`, use `sx` instead.                                                        | `<Stack spacing={2}>...</Stack>`                                    |
| `direction`              | Controls layout direction, especially in `Stack`: `row`, `column`, etc.                                                                         | Not used on form controls like `TextField` or `Button`.                                                                                 | `<Stack direction="row" spacing={2}>...</Stack>`                    |
| `container`              | Used with `Grid` to say “this Grid is a wrapper for grid items.”                                                                                | Only used with `Grid`, not with `Box`, `Button`, or `TextField`.                                                                        | `<Grid container spacing={2}>...</Grid>`                            |
| `size` / responsive size | In newer MUI Grid, controls how much width a grid item takes at breakpoints.                                                                    | Grid-specific usage. Do not confuse it with `Button size`.                                                                              | `<Grid size={{ xs: 12, md: 6 }}>Left</Grid>`                        |
| `alignItems`             | Aligns children on the cross axis. Often used with `Box`, `Stack`, or `Grid` through `sx` or direct props.                                      | Not useful on components that do not contain children/layout.                                                                           | `<Stack direction="row" alignItems="center">...</Stack>`            |
| `justifyContent`         | Controls horizontal/primary-axis alignment in flex/grid layouts.                                                                                | Not useful on simple form controls like `TextField`.                                                                                    | `<Box sx={{ display: "flex", justifyContent: "center" }}>...</Box>` |
| `component`              | Changes the underlying HTML element rendered by a MUI component. Useful with `Typography`, `Box`, etc.                                          | Not all components need it. Avoid using it until you understand semantic HTML.                                                          | `<Typography component="h1" variant="h4">Title</Typography>`        |


#### Small Example:

```JavaScript
import {
  Box,
  Button,
  Stack,
  TextField,
  Typography,
} from "@mui/material";

function LoginForm() {
  return (
    <Box
      sx={{
        maxWidth: 400,
        mx: "auto",
        mt: 5,
        p: 3,
        border: "1px solid",
        borderColor: "divider",
        borderRadius: 2,
      }}
    >
      <Stack spacing={2}>
        <Typography variant="h5" component="h1">
          Login
        </Typography>

        <TextField
          label="Email"
          type="email"
          required
          fullWidth
          helperText="Enter your email address"
        />

        <TextField
          label="Password"
          type="password"
          required
          fullWidth
        />

        <Button
          variant="contained"
          color="primary"
          size="large"
          fullWidth
        >
          Sign In
        </Button>
      </Stack>
    </Box>
  );
}
```

----

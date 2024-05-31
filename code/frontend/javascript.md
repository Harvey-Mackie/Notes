# General JavaScript Syntax


## Useful JavaScript Commands

- **slice** - Get the first 'x' elements of an array - `blogs.slice(0,9)`

# React

## Create React App

```
npx create-react-app my-app --template typescript

```

## VS Code Commands

- To create a stateless functional component with default export - `tsdrpfc`

## TypeScript

### Routing

Use the `react-router-dom` package for routing. Then add it to `App.tsx`

```tsx
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom'
function App () {
  return (
    <div className='App'>
      <Router>
        <Routes>
          <Route path='/' element={<HomePage />} />
        </Routes>
      </Router>
    </div>
  )
}
export default App

```

The one drawback of `react-router-dom` is that it doesn't handle links that navigate to a section (`index.html#Blog`)

`npm i --save-dev @types/react-router-hash-link`

```jsx
<NavHashLink className={styles.navItems} key={item} to={`/#${item}`}>
	{item}
</NavHashLink>

```

### Parameters

```tsx
export interface IAboutProps {
	name: String
}

export default function About (props: IAboutProps) {
	// Return component
}

```

## Icons

An easy way to use Icons is to use the `react-icons` library. You can then view all the options of icons on this [React Icons (react-icons.github.io)](https://react-icons.github.io/react-icons/)
)

```jsx
import { IconName } from "react-icons/fa";

...

<IconName/>

```

## Material UI

### Set-up

- General `npm install @material-ui/core`
- Get the font - `npm install @fontsource/roboto`

### Adding Styles

Make use of the `useStyles` and `makeStyles` hooks.

```tsx
import {makeStyles} from '@material-ui/core'

const useStyles = makeStyles(theme => ({
  buttonContainer: {
    '& button': {
      marginRight: '1rem'
    }
  }
}))

export interface IAboutProps {}

export default function About(props:IAboutProps){
	const styles = useStyles();

	return <div className={styles.buttonContainer}> Testing </div>
}

```

### Grid

Can add properties such as `direction`, `alignItems`, `justifyContent` etc.

```tsx
<Grid container style={{ padding: '1rem' }}>
	<Grid item xs={6}>
	</Grid>

	<Grid item xs={6}>
	</Grid>
</Grid>

```

### Text (Typography)

```tsx
z

```

## Code Snippets/Implementations

### Requests (API Connect)

**TLDR**

- Create a common function called `fetching` to route all requests through - accepting URL, headers etc.
- Call `fetching` method from class named after domain/controller e.g. `blog`
- Add call to `blog` in `component` and set response to a state variable

**components/component.ts**

```jsx
export default function BlogList(){
	const [blogs, setBlogs] = useState<BlogSummary[]>();

	async function initBlogs(){
	    const blogsResponse = await GetBlogs();
	    setBlogs(blogsResponse);
	  }

	return (<div>{blogs.map(blog => blog.name)})
}

```

**api/blog.ts**

```jsx
import { HTTP_METHOD, fetching } from "./common";

export async function GetBlogs(){
    return await fetching("", HTTP_METHOD.GET, undefined, true, undefined);
}

export async function addBlog(title?:string, summary?:string, image?: string, content?: string){
  const body = {
    title: title,
    summaryContent: summary,
    summaryPicture: image,
    articleContent: content,
  };

  return await fetching("", HTTP_METHOD.POST, body, true, 'Successfully Added Blog - Navigating Now');
}

```

**api/common.ts**

```jsx
import { errorToast, successToast } from "../utils/utils";

const GENERIC_HEADERS = {
    'Content-Type': 'application/json',
    'Accept': 'application/json, text/plain, */*'
}

export const HTTP_METHOD = {
    PUT: "PUT",
    GET: "GET",
    POST: "POST",
    PATCH: "PATCH",
}

export const fetching = async <T>(
	path: string,
	method = "GET",
	body?: T,
	includeHeaders = false,
	successMessage?:string) => {

	const url = buildApiUrl(path)
    const response = await fetch(url, {
        method: method,
        headers: includeHeaders ? GENERIC_HEADERS : undefined,
        body: body ? JSON.stringify(body) : undefined
    })

    const responseJson = await response.json();
    if(!response.ok){
      errorToast(responseJson ? responseJson.message : "Error Occured");
      return;
    }

    if(successMessage){
        successToast(successMessage);
    }

    return responseJson.content;
}

export const buildApiUrl = (path: string): string => `http://localhost:8080/${path}`;

```

### Form Management (`Formik`)

**TLDR**

- Create `validate` and `onsubmit` methods
- Wrap form around `Formik` tags then render the form passing the appropriate parameters e.g. `values`, `errors`, `handleSubmit`

**Methods**

```jsx
function validate(values : FormikValues){
	const errors = {} as BlogAdd;
	const imageRegex = /\\.(jpeg|jpg|gif|png)$/i;

	if (!values.title) {
		errors.title = 'Required';
	} else if (values.title.length > 254) {
		errors.title = 'Title is too long (maximum 254 characters)';
	}
	if (!values.summaryImageLink) {
		errors.summaryImageLink = 'Required';
	} else if (!/^(https?:\\/\\/)?[\\w-]+(\\.[\\w-]+)+[\\w-]+(\\/[\\w- ;,./?%&=]*)?$/i.test(values.summaryImageLink)) {
		errors.summaryImageLink = 'Invalid URL';
	}
	else if (!imageRegex.test(values.summaryImageLink)) {
	  errors.summaryImageLink = 'Invalid image URL';
	}
	return errors;
}

const onSubmit = async (values: BlogAdd, { setSubmitting, resetForm  }: FormikHelpers<BlogAdd>) =>{
  await addBlog(values.title, values.summary, values.summaryImageLink, values.blogText);
  setSubmitting(false);
  resetForm();
};

```

**Render Component**

```jsx
<Formik
  initialValues={{ title: '', summary: '', summaryImageLink: '', blogText: '' }}
  validate={validate}
  onSubmit={onSubmit}
>

	{({
	  values,
	  errors,
	  touched,
	  handleChange,
	  handleBlur,
	  handleSubmit
	}) => (

	<form className={styles.subscribeContainerForm} onSubmit={handleSubmit}>
		<TextField
		  name="title"
		  label='Title'
		  variant="filled"
		  onChange={handleChange}
		  onBlur={handleBlur}
		  value={values.title}
		  helperText={errors.title}
		  error={touched.title && errors.title != undefined}
		  inputProps={{ maxLength: 254 }}
		/>

		<TextField
			inputProps={{ maxLength: 254 }}
			type='text'
			multiline={true}
			minRows={3}
			label='Summary Text'
			name="summary"
			onChange={handleChange}
			onBlur={handleBlur}
			value={values.summary}
			error={touched.summary && errors.summary != undefined}
			helperText={touched.summary && errors.summary}
		  />

		  <TextField
			  name="summaryImageLink"
			  label='Summary Image Link'
			  variant="filled"
			  onChange={handleChange}
			  onBlur={handleBlur}
			  value={values.summaryImageLink}
			  helperText={touched.summaryImageLink && errors.summaryImageLink}
			  error={touched.summaryImageLink && errors.summaryImageLink != undefined}
			  inputProps={{ maxLength: 600 }}
		  />

		<MDEditor
		  textareaProps={{name: 'blogText'}}
		  height={700}
		  value={values.blogText}
		  onChange={(value, event) => handleChange(event)}
		  style={{border: touched.blogText && errors.blogText ? "1px solid red" : "none"}}
		/>
		<button type='submit'>Submit</button>
	</form>
	)}
</Formik>

```
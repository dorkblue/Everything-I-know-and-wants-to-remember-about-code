# Everything-I-know-and-wants-to-remember-about-code
A dumpster for code related stuff, will reorganize in the future.


### Redeploy to Heroku without changes
> git commit --allow-empty -m "Message here!"
> git push heroku master

### Passing props to React children or prop element using React.cloneElement
https://stackoverflow.com/questions/32370994/how-to-pass-props-to-this-props-children
```
<Modal
 formComponent={<RandomForm />}
/>

class Modal extends React.Component {
  constructor(props) {
   super(props)
   this.state = {}
   this.someRefHandler = this.someRefHandler.bind(this)
  }

  someRefHandler (ref) {
    this.form = ref
  }

  render() {
    return (
      { React.cloneElement(this.props.formComponent, { someRefHandler }) }
    )
  }
}

const RandomForm = ({ someRefHandler }) => {
 return (
  <form
   ref={
    ref => someRefHandler(ref)}
  >
   <input />
  </form>
 )
         
}
```

### Mongoose: compare ObjectId and objectId string
> ObjectId.equals(stringId)


### CRA HEROKU 404 Not Found NGINX Issue
Include static.json file in root https://github.com/mars/create-react-app-buildpack#customization

```
{ 
	"root": "build/",
 	"routes": {
	  "/**": "index.html"
	},
	"https_only": true
}

```

### Creating Array with length according to a number
```
Array.from(new Array(quantity))
```

### Storing Multiline Text, and displaying Multiline Text in HTML
```
	<p style={{ whiteSpace: 'pre-line' }}>
		{'Hello Robin\n\n\nI can enter next line\n\n- addon 1\n- addon 2'}
	</p>
```

## "Break out" of a parent's containing width to take the full screen of a page w/this nice utility class:

```
.full-width {
  width: 100vw;
  position: relative;
  left: 50%;
  right: 50%;
  margin-left: -50vw;
  margin-right: -50vw;
}
```

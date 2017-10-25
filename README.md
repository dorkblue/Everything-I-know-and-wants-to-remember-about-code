# Everything-I-know-and-wants-to-remember-about-code
A dumpster for code related stuff, will reorganize in the future.


### Redeploy to Heroku without changes
> git commit --allow-empty -m "Message here!"
> git push heroku master

### Passing props to React children or prop element
> ```
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
```

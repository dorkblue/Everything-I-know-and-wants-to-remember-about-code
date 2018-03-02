# Everything-I-know-and-wants-to-remember-about-code
A dumpster for code related stuff, will reorganize in the future.

### Design Cheat sheets
https://codepen.io/tyrellrummage/pen/ZJPXgy - Little UI details from @steveschoger

https://medium.com/refactoring-ui/7-practical-tips-for-cheating-at-design-40c736799886 - 7 Practical Tips for Cheating at Design by Adam Wathan & Steve Schoger

https://atomiks.github.io/30-seconds-of-css/ - 30 Seconds of CSS, useful CSS snippets & utility

https://assortment.io/posts/handling-long-titles-with-truncation - Handling long title with truncation


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

### "Break out" of a parent's containing width to take the full screen of a page w/this nice utility class:

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

### Format to two decimals & dealing with floating point
```
Math.round(v * 100) / 100

parseFloat(v).toFixed(2)
```

### Display boundaries of element without affecting layout for debugging
source: https://twitter.com/adamwathan/status/959078631434731521/photo/1
```
* {
 outline: 1px solid red !important;
}

```

### Great color combination for notification boxes
https://isabelcastillo.com/error-info-messages-css
Error
```
 color: #d8000c;
 background-color: #ffbaba;
```

Done / Success
```
 color: #5d872c;
 background-color: #e3f1c4;
```

### Start FTP server on Mac localhost on Bash
To start server
```
sudo -s launchctl load -w /System/Library/LaunchDaemons/ftp.plist
ftp localhost
```

To shut down server
```
exit
sudo -s launchctl unload -w /System/Library/LaunchDaemons/ftp.plist
```

### Create alias (short cmd to run commands) on bash / hyper 
To create new alias
```
alias [name-of-alias]='[command to run]'

ex: alias ftp-launch='sudo -s launchctl load -w /System/Library/LaunchDaemons/ftp.plist'

```

To remove alias
```
unalias [name-of-alias]
```

### Reset `<input type=file />` for React

https://github.com/erikras/redux-form/issues/769
```
<input
 ref={ref => this.fileInput = ref}
/>
```

When running reset function on React / any form reset methods, set
```
this.fileInput && (this.fineInput.value = null)
```

### git push rejected due to tip of current branch behind remote counterpart
https://blog.plover.com/prog/git-ff-error.html

```
	error: failed to push some refs to 'https://git.heroku.com/gto-marinasq.git'
	hint: Updates were rejected because the tip of your current branch is behind
	hint: its remote counterpart. Integrate the remote changes (e.g.
	hint: 'git pull ...') before pushing again.
```

Run in cmd:
```
git fetch origin master
git rebase origin/master
```

May have to fix some conflicts here, when done run
`git add . && git rebase --continue`

and finally
`git push origin master`



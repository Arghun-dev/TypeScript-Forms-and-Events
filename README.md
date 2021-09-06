# TypeScript-Forms-and-Events

to find out the `e` type if you do this, you can easily find => 

```js
onChange={(e) => onChange(e)} // in here if you hover over to the e, you can easily understand the e type
```

```js
import { useState } from 'react';

const defaultFormData = {
  title: "",
  body: ""
}

export default function App() {
  const [formData, setFormData] = useState(defaultFormData);
  const { title, body } = formData;
  
  const onChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    setFormData((prevState) => ({
     ...prevState,
     [e.target.id]: e.target.value,
    }));
  };
  
  const onSubmit = (e: React.FormEvent<HTMLFormElement>) => {
    e.preventDefault();
    console.log(formData);
    
    setFormData(defaultFormData);
  }
  
  return (
    <>
      <h1>Form</h1>
      <p>Create a post</p>
      <form onSubmit={onSubmit}>
        <label htmlFor="title">Title</label>
        <input type="text" id="title" value={title} onChange={onChange} />
        <label htmlFor="body">Body</label>
        <input type="text" id="body" value={body} onChange={onChange} />
        <button type="submit">Upload Post</button>
      </form>
    </>
  )
}
```


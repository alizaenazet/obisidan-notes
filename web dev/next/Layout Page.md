Layout page adalah komponen yang akan ditampilkan pada semua child komponennya 

```jsx
import React from 'react'

  

function BlogLayout({ children }) {
return (
<h1>
<div>BlogLayout</div>
{children}
</h1>
)
}

  

export default BlogLayout
```
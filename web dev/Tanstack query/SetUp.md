- instal package `npm i @tanstack/react-query`

- import `QueryClient` dan `QueryClientProvider` dari `'@tanstack/react-query'`
```jsx
import { QueryClient, QueryClientProvider } from '@tanstack/react-query'
```

- deklrasi class `QueryClient`
```jsx
const queyClient = new QueryClient();
```

- Nest root component didalam `QueryClientProvider` component
```jsx
<QueryClientProvider>
<App />
</QueryClientProvider>
```

- tambahkan objek `QueryClient` pada props(`client` ) komponent `QueryClientProvider` 
```jsx
<QueryClientProvider client={queyClient}>
<App />
</QueryClientProvider>
```

- **Video: **
<iframe width="560" height="315" src="https://www.youtube.com/embed/r8Dg0KVnfMA?clip=UgkxBUNuPKl8dfXGBAeSudckc3RO-MiIxt16&amp;clipt=EMLCCBixzQs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

- contoh lengkap :
```jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'
import { QueryClient, QueryClientProvider } from '@tanstack/react-query'
import './index.css'  


const queyClient = new QueryClient();

ReactDOM.createRoot(document.getElementById('root')).render(
<React.StrictMode>
<QueryClientProvider client={queyClient}>
<App />
</QueryClientProvider>
</React.StrictMode>,

)
```
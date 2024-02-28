Penggunaan kedua jenis komponen melalui pertimbangan terkait kemampuan dari masing-masing kedua komponen tersebut, berikut perbedaan fungsional :
![[Screenshot 2023-05-21 at 19.33.13.png]]

## point intisari :
- perioritaskan penggunaan server komponen (selagi memungkinkan)
- apabila komponen memiliki interaksi seperti (`onClick`, `useEffect`, `reactHook`) maka gunakan client komponen
- perbedaan menonjol diantara keduanya adalah penggunaan dalam mengelola data seperti fetching api 

## Server component vs Client component

Perbedaan menonjol adalah cara melakukan fethcing data :
1. Fetching data pada Server component
2. Fetching data pada Client component

![[Screenshot 2023-05-21 at 19.40.50.png]]


### Client component 
```jsx
import Link from 'next/link';
import useSWR from 'swr'

const fetcher = (url: string) => fetch(url).then(r => r.json())

interface Props{
users : string
}

export default function UsersList({users}:Props) {

const {data, error} = useSWR(` https://api.github.com/search/users?q=${users}`,fetcher);

const isLoading = !data && !error

return(
<div>
{isLoading && <p>Loading...</p>}
<ul>
{data && data.items.map((user:any, index:number) =>{
return(
<li key={index}> <Link href={`/search/${user.login}`}>{user.login}</Link>
<ul>
<li> <Link href={user.html_url}>Visit github profile</Link> </li>
</ul>
</li>
)

})}
</ul>
</div>
)
}
```

### Server component 
```jsx

export default async function searchUser({ params }: { params: { slug: string } }) {
const posts = await fetch(` https://api.github.com/users/${params.slug}`).then((res) => res.json());
const datas = Object.entries(posts);
return(
<>
<ul>
{datas.map((key) => {
return(
<li style={{margin:"1em 0"}}>{key[0] }
<ul><li>{`${key[1]}`}</li></ul>
</li>
)
})}
</ul>
</>
)

}
```


# Share to Social Media
In case of share something from our web application to various social media, we can follow 2 systems in ReactJS/NextJS. 
- With custom function
- With extra package

## Custom
### Technologies
- ReactJS/NextJS
- TailwindCSS
- React-icons

#### Import:
```jsx
  import { BsFacebook, BsLinkedin } from 'react-icons/bs';
  import { FaXTwitter } from "react-icons/fa6";
```

#### In Function:
```jsx
    const [url, setUrl] = useState('');

    useEffect(() => {
      setUrl(window.location.href);
    }, []);
```

#### In Return:
```jsx
    <a href={`https://www.facebook.com/sharer.php?u=${url}`} target="_blank" rel="noopener noreferrer" className="bg-blue-50 p-3 rounded-full text-blue-500">
      <BsFacebook />
    </a>
    <a href={`https://twitter.com/share?url=${url}`} target="_blank" rel="noopener noreferrer" className="bg-gray-50 p-3 rounded-full text-gray-800">
      <FaXTwitter />
    </a>
    <a href={`https://www.linkedin.com/sharing/share-offsite/?url=${url}`} target="_blank" rel="noopener noreferrer" className="bg-blue-50 p-3 rounded-full text-blue-500">
      <BsLinkedin />
    </a>
```

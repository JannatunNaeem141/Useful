# Copy to clipboard by clicking
We used to copy to clipboard by clicking the copy button. It increases the user experience. This is how we can make this easily…

## Technologies
- ReactJS
- TailwindCSS
- React Icons

## Import: 
```jsx
  import React, { useRef } from 'react';
  import { AiOutlineCheck } from 'react-icons/ai';
  import { MdContentCopy } from 'react-icons/md';
```

### In Function :
```jsx
  const link = 'https://example.com';
  const inputRef = useRef(null);
  const [copied, setCopied] = useState(false);


  const handleCopyLink = () => {
    if (navigator.clipboard) {
      navigator.clipboard.writeText(link);
    } else {
      inputRef.current.select();
      document.execCommand('copy');
    }
    setCopied(true);
    setTimeout(() => {
      setCopied(false);
    }, 2000);
  };
```

### In Return :
```jsx
  return (
    <div className='flex'>
        <div className="flex items-center bg-blue-50 p-2 rounded-lg">
            <p className="mr-2">{link}</p>
            <input
                type="text"
                ref={inputRef}
                value={link}
                className="opacity-0 w-0 h-0"
                readOnly
            />
            <button
                onClick={handleCopyLink}
                className="p-2 rounded-md bg-gray-300 hover:bg-gray-400"
            >
                {copied ? (
                <AiOutlineCheck className="text-green-500" />
                ) : (
                <MdContentCopy className="text-gray-600" />
                )}
            </button>
        </div>
    </div>
  )
```

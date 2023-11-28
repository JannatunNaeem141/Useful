# Bangla & English Regex
In case of loading data from backend, we don’t know which font is that. As we don’t know the language of the data, we will not be able to change the different FontStyle for different language. To solve this problem we can use the various language Regex. Here I am showing English and Bangla Regex.

## Technologies
- ReactJS
- TailwindCSS

### In Function :
```jsx
  function isBangla(text) {
      const banglaCharRegex = /[\u0980-\u09FF]/;
      return banglaCharRegex.test(text);
  }
  function isEnglish(text) {
      const englishCharRegex = /[a-zA-Z]/;
      return englishCharRegex.test(text);
  }
```

### In Return :
```jsx
  return (
    <p
       className={`${
          isBangla(data?.description) ? 'banglaFont' : ''
       }`}
    >
       {data?.description}
    </p>
)
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

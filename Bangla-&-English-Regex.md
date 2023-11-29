# Bangla & English Regex
In case of loading data from backend, we don’t know which font is that. As we don’t know the language of the data, we will not be able to change the different FontStyle for different language. To solve this problem we can use the various language Regex. Here I am showing English and Bangla Regex.

## Technologies
- ReactJS/NextJS
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

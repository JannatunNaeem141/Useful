# Encrypted Password

## Install Package
```jsx
  npm install crypto-js
```

## Import
```jsx
  import sha256 from 'crypto-js/sha256';
```

## Function
```jsx
    const password = '123456';
    const hashedPassword = sha256(password).toString();
    console.log(hashedPassword);
```

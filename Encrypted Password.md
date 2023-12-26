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
  const onSubmit = data => {
    const hashedPassword = sha256(data.password).toString();
  }
```

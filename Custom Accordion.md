# Custom Accordion
This is a custom accordion for frequently asked questions.

## Technologies
- ReactJS/NextJS
- TailwindCSS & CSS
- React Icons

## Import
```jsx
  import { HiMinus, HiPlus } from 'react-icons/hi';
```

## Functions
```jsx
    const [activeIndex, setActiveIndex] = useState(null);

  const handleClick = (index) => {
    if (index === activeIndex) {
      setActiveIndex(null);
    } else {
      setActiveIndex(index);
    }
  };

```

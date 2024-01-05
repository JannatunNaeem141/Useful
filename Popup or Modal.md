# Popup or Modal
This will show when user will come first time in the website or reload the home page.

## Technologies
- ReactJS/NextJS
- TailwindCSS & Custom CSS

## In Function
```jsx
  const [showModal, setShowModal] = useState(false);

  useEffect(() => {
    const isFirstVisit = localStorage.getItem('isFirstVisit');
    if (!isFirstVisit) {
      setShowModal(true);
      localStorage.setItem('isFirstVisit', 'false');
    }
  }, []);
  useEffect(() => {
    window.addEventListener('beforeunload', () => {
      localStorage.removeItem('isFirstVisit');
    });
  }, []);

```

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

## In Return:
```jsx
  <div className='flex justify-center items-center'>
      <div className='z-50 absolute top-24'>
          {showModal && (
              <div className='modal-overlay'>
                  <div className="modal-content">
                      <button onClick={() => setShowModal(false)} className='absolute right-1 top-1 bg-white hover:bg-slate-200 transition-all p-2 rounded-full'>Close</button>
                      <div>
                        White popup content here
                      </div>
                  </div>
              </div>
          )}
      </div>
  </div>
```

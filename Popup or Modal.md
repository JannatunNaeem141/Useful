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

## In CSS
```jsx
  .modal-content {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: white;
    border-radius: 10px;
    padding: 15px;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
  }
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  
  @media (min-width: 320px) and (max-width: 480px) {
      .modal-content {
          right: -35%;
      }
  }
```

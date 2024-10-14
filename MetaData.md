# Meta Data
For website SEO purpose, we have to use the meta data. Here providing a standard meta structure for raw HTML project and also for JSX project.

### In HTML :
```jsx
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>This is Title</title>
    <meta name="description" content="" />
    <meta name="author" content="" />
    <meta name="keywords" content="" />
    <meta name="robots" content="index, follow" />
    <meta name="googlebot" content="index, follow" />
    <meta name="whatsapp:label" content="" />
    <meta name="whatsapp:text" content="" />
    <meta name="google" content="translate" />
    <meta name="google" content="sitelinkssearchbox" />
    <meta property="og:title" content="" />
    <meta property="og:description" content="" />
    <meta property="og:url" content="https://example.com/" />
    <meta property="og:site_name" content="" />
    <meta property="og:image" content="" />
    <meta property="og:image:alt" content="" />
    <meta property="og:type" content="website" />
    <meta name="twitter:card" content="summary_large_image" />
    <meta name="twitter:title" content="" />
    <meta name="twitter:description" content="" />
    <meta name="twitter:image" content="" />
```

### In JSX (Ex: NextJS app router) :
```jsx
export const metadata = {
  title: '',
  description: '',
  keywords: [],
  authors: [{ name: '' }],
  icons: {
    icon: '/favicon.ico',
  },
  openGraph: {
    type: 'website',
    url: '',
    title: '',
    description: '',
    siteName: '',
    images: [
      {
        url: '',
        alt: '',
      },
    ],
  },
  twitter: {
    card: 'summary_large_image',
    title: '',
    description: '',
    images: [],
  },
  other: {
    'whatsapp:label': '',
    'whatsapp:text': '',
    google: ['translate', 'sitelinkssearchbox'],
  },
  robots: {
    index: true,
    follow: true,
    googleBot: {
      index: true,
      follow: true,
    },
  },
};
```

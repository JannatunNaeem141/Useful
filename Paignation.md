# Custom Pagenation


## Index.tsx: 
```jsx
  'use client';
  
  import Pagination2 from '@/components/Pagination2';
  import { useState } from 'react';
  
  const Index = () => {
    const [currentPage, setCurrentPage] = useState(1);
    const ITEMS_PER_PAGE = 10;
    const items = Array.from({ length: 200 }, (_, i) => `Item ${i + 1}`);
    const totalPages = Math.ceil(items.length / ITEMS_PER_PAGE);
  
    const handlePageChange = (page: number) => {
      if (page > 0 && page <= totalPages) {
        setCurrentPage(page);
      }
    };
  
    const startIndex = (currentPage - 1) * ITEMS_PER_PAGE;
    const currentItems = items.slice(startIndex, startIndex + ITEMS_PER_PAGE);
    return (
      <div className='container mx-auto p-4'>
        <ul>
          {currentItems.map((item) => (
            <li key={item} className='p-2 border-b border-gray-200'>
              {item}
            </li>
          ))}
        </ul>
        <Pagination2 currentPage={currentPage} totalPages={totalPages} onPageChange={handlePageChange} />
      </div>
    );
  };
  
  export default Index;
```
## Pagination.tsx:
```jsx
interface propsType {
  currentPage: number;
  totalPages: number;
  onPageChange: (page: number) => void;
}

const Pagination = ({ currentPage, totalPages, onPageChange }: propsType) => {
    const getVisiblePages = () => {
      if (totalPages <= 5) {
        return Array.from({ length: totalPages }, (_, i) => i + 1);
      }
  
      const startPage = Math.max(2, currentPage - 1);
      const endPage = Math.min(totalPages - 1, currentPage + 1);
  
      let pages = [1];
  
      if (startPage > 2) {
        pages.push(-1);
      }
  
      for (let i = startPage; i <= endPage; i++) {
        pages.push(i);
      }
  
      if (endPage < totalPages - 1) {
        pages.push(-1);
      }
  
      pages.push(totalPages);
  
      return pages;
    };
  
    const visiblePages = getVisiblePages();
  
    return (
      <div className='flex justify-center mt-4'>
        <nav className='inline-flex rounded-md shadow-sm' aria-label='Pagination'>
          <button onClick={() => onPageChange(currentPage - 1)} disabled={currentPage === 1} className='px-4 py-2 border border-gray-300 text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 disabled:opacity-50 disabled:cursor-not-allowed'>
            Previous
          </button>
          {visiblePages.map((page, index) => (
            <button key={index} onClick={() => page > 0 && onPageChange(page)} disabled={page === -1} className={`px-4 py-2 border border-gray-300 text-sm font-medium ${page === currentPage ? 'bg-indigo-500 text-white' : 'text-gray-700 bg-white hover:bg-gray-50'} ${page === -1 ? 'disabled:cursor-default' : ''}`}>
              {page > 0 ? page : '...'}
            </button>
          ))}
          <button onClick={() => onPageChange(currentPage + 1)} disabled={currentPage === totalPages} className='px-4 py-2 border border-gray-300 text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 disabled:opacity-50 disabled:cursor-not-allowed'>
            Next
          </button>
        </nav>
      </div>
    );
  };
  
  export default Pagination;

```

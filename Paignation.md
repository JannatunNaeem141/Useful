# Custom Pagenation
This is a custom pagination system with common component features. This can be styled any way with TailwindCSS. 

## 1. With NextJS/ReactJS
## Technologies
- NextJS/ReactJS
- TypeScript
- TailwindCSS

## Index.tsx: 
```jsx
  'use client';
  
  import Pagination2 from '@/components/Pagination';
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
        <Pagination currentPage={currentPage} totalPages={totalPages} onPageChange={handlePageChange} />
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


# 2. With vanilla JavaScript
## Technologies
- HTML
- TailwindCSS
- JavaScript

## index.html: 
```jsx
  <div
    id="card-container"
    class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 mb-4"
  >
    <!-- Cards will be dynamically inserted here -->
  </div>

  <div class="flex justify-center space-x-2 mt-4">
    <button
      id="first-btn"
      class="px-3 py-1 bg-gray-300 text-gray-800 rounded hover:bg-gray-400"
    >
      <<
    </button>
    <button
      id="prev-btn"
      class="px-3 py-1 bg-gray-300 text-gray-800 rounded hover:bg-gray-400"
    >
      <
    </button>
    <div id="page-buttons" class="flex space-x-1"></div>
    <button
      id="next-btn"
      class="px-3 py-1 bg-gray-300 text-gray-800 rounded hover:bg-gray-400"
    >
      >
    </button>
    <button
      id="last-btn"
      class="px-3 py-1 bg-gray-300 text-gray-800 rounded hover:bg-gray-400"
    >
      >>
    </button>
  </div>
```
## script.js:
```jsx
  const cards = [
    { title: "Card 1", content: "This is card 1 content." },
    { title: "Card 2", content: "This is card 2 content." },
    { title: "Card 3", content: "This is card 3 content." },
    { title: "Card 4", content: "This is card 4 content." },
    { title: "Card 5", content: "This is card 5 content." },
    { title: "Card 6", content: "This is card 6 content." },
    { title: "Card 7", content: "This is card 7 content." },
    { title: "Card 8", content: "This is card 8 content." },
    { title: "Card 9", content: "This is card 9 content." },
    { title: "Card 10", content: "This is card 10 content." },
    { title: "Card 11", content: "This is card 11 content." },
    { title: "Card 12", content: "This is card 12 content." },
    { title: "Card 12", content: "This is card 13 content." },
    { title: "Card 12", content: "This is card 14 content." },
  ];
  
  const cardsPerPage = 4;
  let currentPage = 1;
  
  function renderCards(page) {
    const startIndex = (page - 1) * cardsPerPage;
    const endIndex = startIndex + cardsPerPage;
    const cardsToShow = cards.slice(startIndex, endIndex);
  
    const cardContainer = document.getElementById("card-container");
    cardContainer.innerHTML = cardsToShow.map(
        (card) => `
            <div class="p-4 bg-white rounded-lg shadow">
                <h3 class="text-lg font-semibold">${card.title}</h3>
                <p class="text-gray-600">${card.content}</p>
            </div>
        `
      ).join("");
    renderPagination();
  }
  
  function renderPagination() {
    const totalPages = Math.ceil(cards.length / cardsPerPage);
    const pageButtonsContainer = document.getElementById("page-buttons");
    pageButtonsContainer.innerHTML = "";
  
    for (let i = 1; i <= totalPages; i++) {
      const pageButton = document.createElement("button");
      pageButton.textContent = i;
      pageButton.className = `px-3 py-1 ${
        currentPage === i
          ? "bg-blue-500 text-white"
          : "bg-gray-300 text-gray-800"
      } rounded hover:bg-gray-400`;
      pageButton.addEventListener("click", () => {
        currentPage = i;
        renderCards(currentPage);
      });
      pageButtonsContainer.appendChild(pageButton);
    }
  
    document.getElementById("first-btn").disabled = currentPage === 1;
    document.getElementById("prev-btn").disabled = currentPage === 1;
    document.getElementById("next-btn").disabled =
      currentPage === totalPages;
    document.getElementById("last-btn").disabled =
      currentPage === totalPages;
  }
  
  document.getElementById("first-btn").addEventListener("click", () => {
    currentPage = 1;
    renderCards(currentPage);
  });
  
  document.getElementById("prev-btn").addEventListener("click", () => {
    if (currentPage > 1) {
      currentPage--;
      renderCards(currentPage);
    }
  });
  
  document.getElementById("next-btn").addEventListener("click", () => {
    const totalPages = Math.ceil(cards.length / cardsPerPage);
    if (currentPage < totalPages) {
      currentPage++;
      renderCards(currentPage);
    }
  });
  
  document.getElementById("last-btn").addEventListener("click", () => {
    currentPage = Math.ceil(cards.length / cardsPerPage);
    renderCards(currentPage);
  });
  
  // Initial render
  renderCards(currentPage);
```

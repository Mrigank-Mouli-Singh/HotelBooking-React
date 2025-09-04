# Hotel Booking - ReactVite TailwindCSS Fundamental Project 3

<img width="1200" alt="Screenshot 2024-09-13 at 00 01 03" src="https://github.com/user-attachments/assets/51070abc-f3ae-47ef-8bc1-e17151f075da"> ![Screenshot 2024-09-13 at 00 08 31](https://github.com/user-attachments/assets/5b984db0-c8c0-4a9a-bc25-543d30586225) <img width="1200" alt="Screenshot 2024-09-13 at 00 03 29" src="https://github.com/user-attachments/assets/4e1a4f30-ab6a-492a-8607-68963542f151"> ![Screenshot 2024-09-13 at 00 08 53](https://github.com/user-attachments/assets/edbabe77-1879-477d-8711-30bf245ff5b7)

---

## 📖 Project Summary  
**HotelBooking** is a modern, responsive hotel booking frontend application that I built using **React, Vite, and TailwindCSS**.  

The goal of this project was to strengthen my fundamentals in **React (components, context API, hooks)**, while applying **real-world UI/UX practices** such as reusable components, state management, and responsive design.  

I designed it as both a **learning resource** for developers and a **practical template** that can be extended into a full hotel/accommodation booking system.  

🔗 **Live Demo:** [Hotel Booking](https://hotel-booking-arnob.netlify.app)  

---

## 📌 Table of Contents  
- [Project Summary](#-project-summary)  
- [Features](#-features)  
- [Tech Stack & Keywords](#-tech-stack--keywords)  
- [Project Structure](#-project-structure)  
- [Components Overview](#-components-overview)  
- [Pages & Routing](#-pages--routing)  
- [Functionality Walkthrough](#-functionality-walkthrough)  
- [How to Run / Usage Instructions](#-how-to-run--usage-instructions)  
- [Learning Notes](#-learning-notes)  
- [Code Examples](#-code-examples)  
- [Conclusion](#-conclusion)  

---

## ✨ Features  
- 🏨 Responsive hotel booking frontend — fully mobile-ready  
- ⚡ Blazing-fast development experience with **Vite**  
- 🎨 Utility-first design with **TailwindCSS**  
- 🔄 **React Context API** for state management (room filtering, booking flow)  
- 🧩 Reusable components (room cards, booking form, dropdowns, etc.)  
- 📅 Date pickers for check-in / check-out  
- 🚀 Image sliders with **Swiper.js**  
- 🔗 Single Page Application (SPA) navigation with **React Router**  
- 🌀 Loading spinner simulation for data fetching  
- ⬆️ Scroll-to-top on route changes  
- 🛠️ Example hotel data, facilities, and room details  
- ☑️ Hotel rules and booking conditions on room details page  

---

## 🛠️ Tech Stack & Keywords  
- **React**, **Vite**, **React Router DOM**  
- **TailwindCSS**, **PostCSS**, **Autoprefixer**  
- **Context API**, **Hooks** (useState, useContext, useParams)  
- **React Date Picker**, **Swiper**, **Spinners**  
- **Responsive Design**, **SPA Architecture**  

---

## 📂 Project Structure  
HotelBooking/
├── public/ # Favicon & static assets
├── src/
│ ├── assets/ # Images & SVGs
│ ├── components/ # UI Components
│ ├── constants/ # Static hotel data
│ ├── context/ # React Context (RoomContext.js)
│ ├── pages/ # Page-level components
│ ├── utils/ # Utility helpers (ScrollToTop)
│ ├── App.jsx # Main App component + routing
│ ├── main.jsx # App entry point
│ └── index.css # TailwindCSS directives
├── index.html
├── package.json
├── tailwind.config.js
├── postcss.config.js
└── README.md

markdown
Copy code

---

## 🧩 Components Overview  
- **Header** – Navigation bar with logo & links  
- **Footer** – App footer  
- **HeroSlider** – Swiper slider for hotel images  
- **BookForm** – Main booking form (dates, guests)  
- **Rooms** – Grid of available rooms  
- **Room** – Individual room card component  
- **RoomDetails** – Full details of selected room  
- **Dropdowns** – AdultsDropdown, KidsDropdown  
- **CheckIn / CheckOut** – Date pickers  
- **PageNotFound** – 404 fallback  
- **ScrollToTop** – Utility to handle route changes  

---

## 🌐 Pages & Routing  
- `/` – Homepage: hero slider, booking form, room listing  
- `/room/:id` – Room details page  
- `*` – PageNotFound  

Routing handled via **react-router-dom** in `App.jsx`.  

---

## 🎮 Functionality Walkthrough  
### Homepage (`/`)  
- HeroSlider with hotel images  
- BookForm: check-in, check-out, guests (state via context)  
- Rooms Grid: dynamic listing of rooms  

### Room Details (`/room/:id`)  
- Room images, description, facilities, and price  
- Booking section (with guest/date selectors)  
- Hotel rules and policies  

### Spinner Loading  
- Full-screen spinner when data is “loading”  

### Responsive Design  
- Mobile-first approach with TailwindCSS utility classes  
- Adaptive layouts for small and large screens  

---

## ▶️ How to Run / Usage Instructions  

1. **Clone the Repository**
```bash
git clone https://github.com/Mrigank-Mouli-Singh/HotelBooking-React.git
cd HotelBooking-React
Install Dependencies

bash
Copy code
npm install
Run the Development Server

bash
Copy code
npm run dev
Open: http://localhost:5173

📚 Learning Notes
Practiced Context API for global state management.

Built reusable UI components to encourage modular design.

Used TailwindCSS for rapid styling without CSS files.

Learned declarative routing and dynamic params with React Router.

Explored third-party libraries like date pickers, spinners, and sliders.

Gained experience in deploying React + Vite apps to Netlify.

🧾 Code Examples
App Routing (src/App.jsx)
jsx
Copy code
import { BrowserRouter, Route, Routes } from 'react-router-dom';
import { Footer, Header, PageNotFound } from './components';
import { Home, RoomDetails } from './pages';

const App = () => (
  <main>
    <BrowserRouter>
      <Header />
      <Routes>
        <Route path='/' element={<Home />} />
        <Route path='/room/:id' element={<RoomDetails />} />
        <Route path='*' element={<PageNotFound />} />
      </Routes>
      <Footer />
    </BrowserRouter>
  </main>
);

export default App;
Rooms Component (src/components/Rooms.jsx)
jsx
Copy code
import { useRoomContext } from '../context/RoomContext';
import { SpinnerDotted } from 'spinners-react';
import { Room } from '.';

const Rooms = () => {
  const { rooms, loading } = useRoomContext();

  return (
    <section className='py-24'>
      {loading && (
        <div className='h-screen w-full fixed bottom-0 top-0 bg-black/80 z-50 grid place-items-center'>
          <SpinnerDotted />
        </div>
      )}
      <div className='container mx-auto lg:px-0'>
        <div className='text-center'>
          <p className='font-tertiary uppercase text-[15px] tracking-[6px]'>Hotel & Spa Adina</p>
          <h2 className='font-primary text-[45px] mb-6'>Room & Suites</h2>
        </div>
        <div className='grid grid-cols-1 max-w-sm mx-auto gap-[30px] lg:grid-cols-3 lg:max-w-none lg:mx-0'>
          {rooms.map(room => <Room key={room.id} room={room} />)}
        </div>
      </div>
    </section>
  );
};

export default Rooms;

✅ Conclusion
This project demonstrates how to combine React, Vite, and TailwindCSS to build a clean, scalable, and responsive frontend application.

It gave me hands-on practice with state management, routing, and UI libraries, while also serving as a strong foundation for real-world hotel booking or accommodation websites.

🚀 Future Enhancements: Integration with backend APIs, authentication, and real payment flows.

✨ Built with ❤️ and React by Mrigank Mouli Singh
---

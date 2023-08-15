#### Complete App

[Jobify](https://jobify.live/)

#### Create React APP

[VITE](https://vitejs.dev/guide/)

```sh
npm create vite@latest projectName -- --template react
```

#### Vite - Folder and File Structure

```sh
npm i
```

```sh
npm run dev
```

- APP running on http://localhost:5173/
- .jsx extension

#### Remove Boilerplate

- remove App.css
- remove all code in index.css

  App.jsx

```jsx
const App = () => {
  return <h1>Jobify App</h1>;
};
export default App;
```

#### Project Assets

- get assets folder from complete project
- copy index.css
- copy/move README.md (steps)
  - work independently
  - reference
  - troubleshoot
  - copy

#### Global Styles

- saves times on the setup
- less lines of css
- speeds up the development

- if any questions about specific styles
- Coding Addict - [Default Starter Video](https://youtu.be/UDdyGNlQK5w)
- Repo - [Default Starter Repo](https://github.com/john-smilga/default-starter)

#### Title and Favicon

- add favicon.ico in public
- change title and favicon in index.html

```html
<head>
  <link rel="icon" type="image/svg+xml" href="/favicon.ico" />
  <title>Jobify</title>
</head>
```

- resource [Generate Favicons](https://favicon.io/)

#### Install Packages (Optional)

- yes, specific package versions
- specific commands will be provided later
- won't need to stop/start server

```sh
npm install @tanstack/react-query@4.29.5 @tanstack/react-query-devtools@4.29.6 axios@1.3.6 dayjs@1.11.7 react-icons@4.8.0 react-router-dom@6.10.0 react-toastify@9.1.2 recharts@2.5.0 styled-components@5.3.10

```

#### Router

[React Router](https://reactrouter.com/en/main)

- version 6.4 brought significant changes (loader and action)
- pages as independent entities
- less need for global state
- more pages

#### Setup Router

- all my examples will include version !!!

```sh
npm i react-router-dom@6.10.0
```

App.jsx

```jsx
import { createBrowserRouter, RouterProvider } from 'react-router-dom';

const router = createBrowserRouter([
  {
    path: '/',
    element: <h1>home</h1>,
  },
  {
    path: '/about',
    element: (
      <div>
        <h2>about page</h2>
      </div>
    ),
  },
]);

const App = () => {
  return <RouterProvider router={router} />;
};
export default App;
```

#### Create Pages

- create src/pages directory
- setup index.js and following pages :

  AddJob.jsx
  Admin.jsx
  AllJobs.jsx
  DashboardLayout.jsx
  DeleteJob.jsx
  EditJob.jsx
  Error.jsx
  HomeLayout.jsx
  Landing.jsx
  Login.jsx
  Profile.jsx
  Register.jsx
  Stats.jsx

```jsx
const AddJob = () => {
  return <h1>AddJob</h1>;
};
export default AddJob;
```

#### Index

App.jsx

```jsx
import HomeLayout from '../ pages/HomeLayout';
```

pages/index.js

```js
export { default as DashboardLayout } from './DashboardLayout';
export { default as Landing } from './Landing';
export { default as HomeLayout } from './HomeLayout';
export { default as Register } from './Register';
export { default as Login } from './Login';
export { default as Error } from './Error';
export { default as Stats } from './Stats';
export { default as AllJobs } from './AllJobs';
export { default as AddJob } from './AddJob';
export { default as EditJob } from './EditJob';
export { default as Profile } from './Profile';
export { default as Admin } from './Admin';
```

App.jsx

```jsx
import {
  HomeLayout,
  Landing,
  Register,
  Login,
  DashboardLayout,
  Error,
} from './pages';

const router = createBrowserRouter([
  {
    path: '/',
    element: <HomeLayout />,
  },
  {
    path: '/register',
    element: <Register />,
  },
  {
    path: '/login',
    element: <Login />,
  },
  {
    path: '/dashboard',
    element: <DashboardLayout />,
  },
]);
```

#### Link Component

- navigate around project
- client side routing

Register.jsx

```jsx
import { Link } from 'react-router-dom';

const Register = () => {
  return (
    <div>
      <h1>Register</h1>
      <Link to='/login'>Login Page</Link>
    </div>
  );
};
export default Register;
```

Login.jsx

```jsx
import { Link } from 'react-router-dom';

const Login = () => {
  return (
    <div>
      <h1>Login</h1>
      <Link to='/register'>Register Page</Link>
    </div>
  );
};
export default Login;
```

#### Nested Routes

- what about Navbar?
- decide on root (parent route)
- make path relative
- for time being only home layout will be visible

App.jsx

```jsx
const router = createBrowserRouter([
  {
    path: '/',
    element: <HomeLayout />,
    children: [
      {
        path: 'register',
        element: <Register />,
      },
      {
        path: 'login',
        element: <Login />,
      },
      {
        path: 'dashboard',
        element: <DashboardLayout />,
      },
    ],
  },
]);
```

HomeLayout.jsx

```jsx
import { Outlet } from 'react-router-dom';

const HomeLayout = () => {
  return (
    <>
      {/* add things like Navbar */}
      {/* <h1>home layout</h1> */}
      <Outlet />
    </>
  );
};
export default HomeLayout;
```

#### Index (Home) Page

App.jsx

```jsx
{
    path: '/',
    element: <HomeLayout />,
    children: [
      {
        index: true,
        element: <Landing />,
      },
...
      ]
}
```

#### Error Page

- bubbles up

App.jsx

```jsx
{
    path: '/',
    element: <HomeLayout />,
    errorElement: <Error />,
    ...
}
```

Error.jsx

```jsx
import { Link, useRouteError } from 'react-router-dom';

const Error = () => {
  const error = useRouteError();
  console.log(error);
  return (
    <div>
      <h1>Error Page !!!</h1>
      <Link to='/dashboard'>back home</Link>
    </div>
  );
};
export default Error;
```

#### Styled Components

- CSS in JS
- Styled Components
- have logic and styles in component
- no name collisions
- apply javascript logic
- [Styled Components Docs](https://styled-components.com/)
- [Styled Components Course](https://www.udemy.com/course/styled-components-tutorial-and-project-course/?referralCode=9DABB172FCB2625B663F)

```sh
npm install styled-components@5.3.10
```

```js
import styled from 'styled-components';

const El = styled.el`
  // styles go here
`;
```

- no name collisions, since unique class
- vscode-styled-components extension
- colors and bugs

Landing.jsx

```jsx
import styled from 'styled-components';

const Landing = () => {
  return (
    <div>
      <h1>Landing</h1>
      <StyledButton>Click Me</StyledButton>
    </div>
  );
};

const StyledButton = styled.button`
  background-color: red;
  color: white;
`;
export default Landing;
```

#### Style Entire React Component

```js
const Wrapper = styled.el``;

const Component = () => {
  return (
    <Wrapper>
      <h1> Component</h1>
    </Wrapper>
  );
};
```

- only responsible for styling
- wrappers folder in assets

Landing.jsx

```jsx
import styled from 'styled-components';

const Landing = () => {
  return (
    <Wrapper>
      <h1>Landing</h1>
      <div className='content'>some content</div>
    </Wrapper>
  );
};

const Wrapper = styled.div`
  background-color: red;
  h1 {
    color: white;
  }
  .content {
    background-color: blue;
    color: yellow;
  }
`;
export default Landing;
```

#### Landing Page

```jsx
import main from '../assets/images/main.svg';
import { Link } from 'react-router-dom';
import logo from '../assets/images/logo.svg';
import styled from 'styled-components';
const Landing = () => {
  return (
    <StyledWrapper>
      <nav>
        <img src={logo} alt='jobify' className='logo' />
      </nav>
      <div className='container page'>
        {/* info */}
        <div className='info'>
          <h1>
            job <span>tracking</span> app
          </h1>
          <p>
            I'm baby wayfarers hoodie next level taiyaki brooklyn cliche blue
            bottle single-origin coffee chia. Aesthetic post-ironic venmo,
            quinoa lo-fi tote bag adaptogen everyday carry meggings +1 brunch
            narwhal.
          </p>
          <Link to='/register' className='btn register-link'>
            Register
          </Link>
          <Link to='/login' className='btn'>
            Login / Demo User
          </Link>
        </div>
        <img src={main} alt='job hunt' className='img main-img' />
      </div>
    </StyledWrapper>
  );
};

const StyledWrapper = styled.section`
  nav {
    width: var(--fluid-width);
    max-width: var(--max-width);
    margin: 0 auto;
    height: var(--nav-height);
    display: flex;
    align-items: center;
  }
  .page {
    min-height: calc(100vh - var(--nav-height));
    display: grid;
    align-items: center;
    margin-top: -3rem;
  }
  h1 {
    font-weight: 700;
    span {
      color: var(--primary-500);
    }
    margin-bottom: 1.5rem;
  }
  p {
    line-height: 2;
    color: var(--text-secondary-color);
    margin-bottom: 1.5rem;
    max-width: 35em;
  }
  .register-link {
    margin-right: 1rem;
  }
  .main-img {
    display: none;
  }
  .btn {
    padding: 0.75rem 1rem;
  }
  @media (min-width: 992px) {
    .page {
      grid-template-columns: 1fr 400px;
      column-gap: 3rem;
    }
    .main-img {
      display: block;
    }
  }
`;

export default Landing;
```

#### Assets/Wrappers

- css optional

  Landing.jsx

```jsx
import Wrapper from '../assets/wrappers/LandingPage';
```

#### Logo Component

- create src/components/Logo.jsx
- import logo and setup component
- in components setup index.js import/export (just like pages)
- replace in Landing

  Logo.jsx

```jsx
import logo from '../assets/images/logo.svg';

const Logo = () => {
  return <img src={logo} alt='jobify' className='logo' />;
};

export default Logo;
```

#### Logo and Images

- logo built in Figma
- [Cool Images](https://undraw.co/)

#### Error Page

Error.jsx

```jsx
import { Link, useRouteError } from 'react-router-dom';
import img from '../assets/images/not-found.svg';
import Wrapper from '../assets/wrappers/ErrorPage';

const Error = () => {
  const error = useRouteError();
  console.log(error);
  if (error.status === 404) {
    return (
      <Wrapper>
        <div>
          <img src={img} alt='not found' />
          <h3>Ohh! page not found</h3>
          <p>We can't seem to find the page you're looking for</p>
          <Link to='/dashboard'>back home</Link>
        </div>
      </Wrapper>
    );
  }
  return (
    <Wrapper>
      <div>
        <h3>something went wrong</h3>
      </div>
    </Wrapper>
  );
};

export default Error;
```

#### Error Page CSS (optional)

assets/wrappers/Error.js

```js
import styled from 'styled-components';

const Wrapper = styled.main`
  min-height: 100vh;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  img {
    width: 90vw;
    max-width: 600px;
    display: block;
    margin-bottom: 2rem;
    margin-top: -3rem;
  }
  h3 {
    margin-bottom: 0.5rem;
  }
  p {
    line-height: 1.5;
    margin-top: 0.5rem;
    margin-bottom: 1rem;
    color: var(--text-secondary-color);
  }
  a {
    color: var(--primary-500);
    text-transform: capitalize;
  }
`;

export default Wrapper;
```

#### Register Page

Register.jsx

```jsx
import { Logo } from '../components';
import Wrapper from '../assets/wrappers/RegisterAndLoginPage';
import { Link } from 'react-router-dom';

const Register = () => {
  return (
    <Wrapper>
      <form className='form'>
        <Logo />
        <h4>Register</h4>
        <div className='form-row'>
          <label htmlFor='name' className='form-label'>
            name
          </label>
          <input
            type='text'
            id='name'
            name='name'
            className='form-input'
            defaultValue='john'
            required
          />
        </div>

        <button type='submit' className='btn btn-block'>
          submit
        </button>
        <p>
          Already a member?
          <Link to='/login' className='member-btn'>
            Login
          </Link>
        </p>
      </form>
    </Wrapper>
  );
};
export default Register;
```

- required attribute

  In HTML, the "required" attribute is used to indicate that a form input field must be filled out before the form can be submitted. It is typically applied to input elements such as text fields, checkboxes, and radio buttons. When the "required" attribute is added to an input element, the browser will prevent form submission if the field is left empty, providing a validation message to prompt the user to enter the required information.

- default value

In React, the defaultValue prop is used to set the initial or default value of an input component. It is similar to the value attribute in HTML, but with a slightly different behavior.

#### FormRow Component

- create components/FormRow.jsx (export/import)

FormRow.jsx

```jsx
const FormRow = ({ type, name, labelText, defaultValue = '' }) => {
  return (
    <div className='form-row'>
      <label htmlFor={name} className='form-label'>
        {labelText || name}
      </label>
      <input
        type={type}
        id={name}
        name={name}
        className='form-input'
        defaultValue={defaultValue}
        required
      />
    </div>
  );
};

export default FormRow;
```

Register.jsx

```jsx
import { Logo, FormRow } from '../components';
import Wrapper from '../assets/wrappers/RegisterAndLoginPage';
import { Link } from 'react-router-dom';

const Register = () => {
  return (
    <Wrapper>
      <form className='form'>
        <Logo />
        <h4>Register</h4>
        <FormRow type='text' name='name' />
        <FormRow type='text' name='lastName' labelText='last name' />
        <FormRow type='text' name='location' />
        <FormRow type='email' name='email' />

        <FormRow type='password' name='password' />

        <button type='submit' className='btn btn-block'>
          submit
        </button>
        <p>
          Already a member?
          <Link to='/login' className='member-btn'>
            Login
          </Link>
        </p>
      </form>
    </Wrapper>
  );
};
export default Register;
```

#### Login Page

Login Page

```jsx
import { Logo, FormRow } from '../components';
import Wrapper from '../assets/wrappers/RegisterAndLoginPage';

import { Link } from 'react-router-dom';

const Login = () => {
  return (
    <Wrapper>
      <form className='form'>
        <Logo />
        <h4>Login</h4>
        <FormRow type='email' name='email' defaultValue='john@gmail.com' />
        <FormRow type='password' name='password' defaultValue='secret123' />
        <button type='submit' className='btn btn-block'>
          submit
        </button>
        <button type='button' className='btn btn-block'>
          explore the app
        </button>
        <p>
          Not a member yet?
          <Link to='/register' className='member-btn'>
            Register
          </Link>
        </p>
      </form>
    </Wrapper>
  );
};
export default Login;
```

#### Register and Login CSS (optional)

assets/wrappers/RegisterAndLoginPage.js

```js
import styled from 'styled-components';

const Wrapper = styled.section`
  min-height: 100vh;
  display: grid;
  align-items: center;
  .logo {
    display: block;
    margin: 0 auto;
    margin-bottom: 1.38rem;
  }
  .form {
    max-width: 400px;
    border-top: 5px solid var(--primary-500);
  }

  h4 {
    text-align: center;
    margin-bottom: 1.38rem;
  }
  p {
    margin-top: 1rem;
    text-align: center;
    line-height: 1.5;
  }
  .btn {
    margin-top: 1rem;
  }
  .member-btn {
    color: var(--primary-500);
    letter-spacing: var(--letter-spacing);
    margin-left: 0.25rem;
  }
`;
export default Wrapper;
```

#### Dashboard Pages

App.jsx

```jsx
 {
        path: 'dashboard',
        element: <DashboardLayout />,
        children: [
          {
            index: true,
            element: <AddJob />,
          },
          { path: 'stats', element: <Stats /> },
          {
            path: 'all-jobs',
            element: <AllJobs />,
          },

          {
            path: 'profile',
            element: <Profile />,
          },
          {
            path: 'admin',
            element: <Admin />,
          },
        ],
      },
```

Dashboard.jsx

```jsx
import { Outlet } from 'react-router-dom';

const DashboardLayout = () => {
  return (
    <div>
      <Outlet />
    </div>
  );
};
export default DashboardLayout;
```

#### Navbar, BigSidebar and SmallSidebar

- in components create :
  Navbar.jsx
  BigSidebar.jsx
  SmallSidebar.jsx

DashboardLayout.jsx

```jsx
import { Outlet } from 'react-router-dom';

import Wrapper from '../assets/wrappers/Dashboard';
import { Navbar, BigSidebar, SmallSidebar } from '../components';

const Dashboard = () => {
  return (
    <Wrapper>
      <main className='dashboard'>
        <SmallSidebar />
        <BigSidebar />
        <div>
          <Navbar />
          <div className='dashboard-page'>
            <Outlet />
          </div>
        </div>
      </main>
    </Wrapper>
  );
};

export default Dashboard;
```

#### Dashboard Layout - CSS (optional)

assets/wrappers/DashboardLayout.jsx

```js
import styled from 'styled-components';

const Wrapper = styled.section`
  .dashboard {
    display: grid;
    grid-template-columns: 1fr;
  }
  .dashboard-page {
    width: 90vw;
    margin: 0 auto;
    padding: 2rem 0;
  }
  @media (min-width: 992px) {
    .dashboard {
      grid-template-columns: auto 1fr;
    }
    .dashboard-page {
      width: 90%;
    }
  }
`;
export default Wrapper;
```

#### Dashboard Context

```jsx
import { Outlet } from 'react-router-dom';

import Wrapper from '../assets/wrappers/Dashboard';
import { Navbar, BigSidebar, SmallSidebar } from '../components';

import { useState, createContext, useContext } from 'react';
const DashboardContext = createContext();
const Dashboard = () => {
  // temp
  const user = { name: 'john' };

  const [showSidebar, setShowSidebar] = useState(false);
  const [isDarkTheme, setIsDarkTheme] = useState(false);

  const toggleDarkTheme = () => {
    console.log('toggle dark theme');
  };

  const toggleSidebar = () => {
    setShowSidebar(!showSidebar);
  };

  const logoutUser = async () => {
    console.log('logout user');
  };
  return (
    <DashboardContext.Provider
      value={{
        user,
        showSidebar,
        isDarkTheme,
        toggleDarkTheme,
        toggleSidebar,
        logoutUser,
      }}
    >
      <Wrapper>
        <main className='dashboard'>
          <SmallSidebar />
          <BigSidebar />
          <div>
            <Navbar />
            <div className='dashboard-page'>
              <Outlet />
            </div>
          </div>
        </main>
      </Wrapper>
    </DashboardContext.Provider>
  );
};

export const useDashboardContext = () => useContext(DashboardContext);

export default Dashboard;
```

#### React Icons

[React Icons](https://react-icons.github.io/react-icons/)

```sh
npm install react-icons@4.8.0
```

Navbar.jsx

```jsx

import {FaHome} from 'react-icons/fa'
const Navbar = () => {
  return (
    <div>
      <h2>navbar</h2>
      <FaHome>
    </div>
  )
}

```

#### Navbar - Initial Setup

```jsx
import Wrapper from '../assets/wrappers/Navbar';
import { FaAlignLeft } from 'react-icons/fa';
import Logo from './Logo';

import { useDashboardContext } from '../pages/DashboardLayout';
const Navbar = () => {
  const { toggleSidebar } = useDashboardContext();
  return (
    <Wrapper>
      <div className='nav-center'>
        <button type='button' className='toggle-btn' onClick={toggleSidebar}>
          <FaAlignLeft />
        </button>
        <div>
          <Logo />
          <h4 className='logo-text'>dashboard</h4>
        </div>
        <div className='btn-container'>toggle/logout</div>
      </div>
    </Wrapper>
  );
};

export default Navbar;
```

#### Navbar CSS (optional)

assets/wrappers/Navbar.js

```js
import styled from 'styled-components';

const Wrapper = styled.nav`
  height: var(--nav-height);
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 1px 0px 0px rgba(0, 0, 0, 0.1);
  background: var(--background-secondary-color);
  .logo {
    display: flex;
    align-items: center;
    width: 100px;
  }
  .nav-center {
    display: flex;
    width: 90vw;
    align-items: center;
    justify-content: space-between;
  }
  .toggle-btn {
    background: transparent;
    border-color: transparent;
    font-size: 1.75rem;
    color: var(--primary-500);
    cursor: pointer;
    display: flex;
    align-items: center;
  }
  .btn-container {
    display: flex;
    align-items: center;
  }

  .logo-text {
    display: none;
  }
  @media (min-width: 992px) {
    position: sticky;
    top: 0;

    .nav-center {
      width: 90%;
    }
    .logo {
      display: none;
    }
    .logo-text {
      display: block;
    }
  }
`;
export default Wrapper;
```

#### Links

- create src/utils/links.jsx

```jsx
import React from 'react';

import { IoBarChartSharp } from 'react-icons/io5';
import { MdQueryStats } from 'react-icons/md';
import { FaWpforms } from 'react-icons/fa';
import { ImProfile } from 'react-icons/im';
import { MdAdminPanelSettings } from 'react-icons/md';

const links = [
  { text: 'add job', path: '.', icon: <FaWpforms /> },
  { text: 'all jobs', path: 'all-jobs', icon: <MdQueryStats /> },
  { text: 'stats', path: 'stats', icon: <IoBarChartSharp /> },
  { text: 'profile', path: 'profile', icon: <ImProfile /> },
  { text: 'admin', path: 'admin', icon: <MdAdminPanelSettings /> },
];

export default links;
```

- in a second, we will discuss why '.' in "add job"

#### SmallSidebar

SmallSidebar

```jsx
import Wrapper from '../assets/wrappers/SmallSidebar';
import { FaTimes } from 'react-icons/fa';

import Logo from './Logo';
import { NavLink } from 'react-router-dom';
import links from '../utils/links';
import { useDashboardContext } from '../pages/DashboardLayout';

const SmallSidebar = () => {
  const { showSidebar, toggleSidebar } = useDashboardContext();
  return (
    <Wrapper>
      <div
        className={
          showSidebar ? 'sidebar-container show-sidebar' : 'sidebar-container'
        }
      >
        <div className='content'>
          <button type='button' className='close-btn' onClick={toggleSidebar}>
            <FaTimes />
          </button>
          <header>
            <Logo />
          </header>
          <div className='nav-links'>
            {links.map((link) => {
              const { text, path, icon } = link;

              return (
                <NavLink
                  to={path}
                  key={text}
                  className='nav-link'
                  onClick={toggleSidebar}
                  // will discuss in a second
                  end
                >
                  <span className='icon'>{icon}</span>
                  {text}
                </NavLink>
              );
            })}
          </div>
        </div>
      </div>
    </Wrapper>
  );
};

export default SmallSidebar;
```

- cover '.' path ,active class and 'end' prop

#### Small Sidebar CSS (optional)

assets/wrappers/SmallSidebar.js

```js
import styled from 'styled-components';

const Wrapper = styled.aside`
  @media (min-width: 992px) {
    display: none;
  }
  .sidebar-container {
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.7);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: -1;
    opacity: 0;
    transition: var(--transition);
    visibility: hidden;
  }
  .show-sidebar {
    z-index: 99;
    opacity: 1;
    visibility: visible;
  }
  .content {
    background: var(--background-secondary-color);
    width: var(--fluid-width);
    height: 95vh;
    border-radius: var(--border-radius);
    padding: 4rem 2rem;
    position: relative;
    display: flex;
    align-items: center;
    flex-direction: column;
  }
  .close-btn {
    position: absolute;
    top: 10px;
    left: 10px;
    background: transparent;
    border-color: transparent;
    font-size: 2rem;
    color: var(--red-dark);
    cursor: pointer;
  }
  .nav-links {
    padding-top: 2rem;
    display: flex;
    flex-direction: column;
  }
  .nav-link {
    display: flex;
    align-items: center;
    color: var(--text-secondary-color);
    padding: 1rem 0;
    text-transform: capitalize;
    transition: var(--transition);
  }
  .nav-link:hover {
    color: var(--primary-500);
  }

  .icon {
    font-size: 1.5rem;
    margin-right: 1rem;
    display: grid;
    place-items: center;
  }
  .active {
    color: var(--primary-500);
  }
`;
export default Wrapper;
```

#### NavLinks

- components/NavLinks.jsx

```jsx
import { useDashboardContext } from '../pages/DashboardLayout';
import links from '../utils/links';
import { NavLink } from 'react-router-dom';

const NavLinks = () => {
  const { user, toggleSidebar } = useDashboardContext();

  return (
    <div className='nav-links'>
      {links.map((link) => {
        const { text, path, icon } = link;
        // admin user
        return (
          <NavLink
            to={path}
            key={text}
            onClick={toggleSidebar}
            className='nav-link'
            end
          >
            <span className='icon'>{icon}</span>
            {text}
          </NavLink>
        );
      })}
    </div>
  );
};

export default NavLinks;
```

#### Big Sidebar

```jsx
import NavLinks from './NavLinks';
import Logo from '../components/Logo';
import Wrapper from '../assets/wrappers/BigSidebar';
import { useDashboardContext } from '../pages/DashboardLayout';

const BigSidebar = () => {
  const { showSidebar } = useDashboardContext();
  return (
    <Wrapper>
      <div
        className={
          showSidebar ? 'sidebar-container ' : 'sidebar-container show-sidebar'
        }
      >
        <div className='content'>
          <header>
            <Logo />
          </header>
          <NavLinks isBigSidebar />
        </div>
      </div>
    </Wrapper>
  );
};

export default BigSidebar;
```

```jsx
const NavLinks = ({ isBigSidebar }) => {
  const { user, toggleSidebar } = useDashboardContext();

  return (
    <div className='nav-links'>
      {links.map((link) => {
        const { text, path, icon } = link;
        // admin user
        return (
          <NavLink
            to={path}
            key={text}
            onClick={isBigSidebar ? null : toggleSidebar}
            className='nav-link'
            end
          >
            <span className='icon'>{icon}</span>
            {text}
          </NavLink>
        );
      })}
    </div>
  );
};

export default NavLinks;
```

#### BigSidebar CSS (optional)

assets/wrappers/BigSidebar.js

```js
import styled from 'styled-components';

const Wrapper = styled.aside`
  display: none;
  @media (min-width: 992px) {
    display: block;
    box-shadow: 1px 0px 0px 0px rgba(0, 0, 0, 0.1);
    .sidebar-container {
      background: var(--background-secondary-color);
      min-height: 100vh;
      height: 100%;
      width: 250px;
      margin-left: -250px;
      transition: margin-left 0.3s ease-in-out;
    }
    .content {
      position: sticky;
      top: 0;
    }
    .show-sidebar {
      margin-left: 0;
    }
    header {
      height: 6rem;
      display: flex;
      align-items: center;
      padding-left: 2.5rem;
    }
    .nav-links {
      padding-top: 2rem;
      display: flex;
      flex-direction: column;
    }
    .nav-link {
      display: flex;
      align-items: center;
      color: var(--text-secondary-color);
      padding: 1rem 0;
      padding-left: 2.5rem;
      text-transform: capitalize;
      transition: padding-left 0.3s ease-in-out;
    }
    .nav-link:hover {
      padding-left: 3rem;
      color: var(--primary-500);
      transition: var(--transition);
    }

    .icon {
      font-size: 1.5rem;
      margin-right: 1rem;
      display: grid;
      place-items: center;
    }
    .active {
      color: var(--primary-500);
    }
  }
`;
export default Wrapper;
```

#### LogoutContainer

components/LogoutContainer.jsx

```jsx
import { FaUserCircle, FaCaretDown } from 'react-icons/fa';
import Wrapper from '../assets/wrappers/LogoutContainer';
import { useState } from 'react';
import { useDashboardContext } from '../pages/DashboardLayout';

const LogoutContainer = () => {
  const [showLogout, setShowLogout] = useState(false);
  const { user, logoutUser } = useDashboardContext();

  return (
    <Wrapper>
      <button
        type='button'
        className='btn logout-btn'
        onClick={() => setShowLogout(!showLogout)}
      >
        {user.avatar ? (
          <img src={user.avatar} alt='avatar' className='img' />
        ) : (
          <FaUserCircle />
        )}

        {user?.name}
        <FaCaretDown />
      </button>
      <div className={showLogout ? 'dropdown show-dropdown' : 'dropdown'}>
        <button type='button' className='dropdown-btn' onClick={logoutUser}>
          logout
        </button>
      </div>
    </Wrapper>
  );
};
export default LogoutContainer;
```

#### LogoutContainer CSS (optional)

assets/wrappers/LogoutContainer.js

```js
import styled from 'styled-components';

const Wrapper = styled.div`
  position: relative;

  .logout-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0 0.5rem;
  }
  .img {
    width: 25px;
    height: 25px;
    border-radius: 50%;
  }
  .dropdown {
    position: absolute;
    top: 45px;
    left: 0;
    width: 100%;
    box-shadow: var(--shadow-2);
    text-align: center;
    visibility: hidden;
    border-radius: var(--border-radius);
    background: var(--primary-500);
  }
  .show-dropdown {
    visibility: visible;
  }
  .dropdown-btn {
    border-radius: var(--border-radius);
    padding: 0.5rem;
    background: transparent;
    border-color: transparent;
    color: var(--white);
    letter-spacing: var(--letter-spacing);
    text-transform: capitalize;
    cursor: pointer;
    width: 100%;
    height: 100%;
  }
`;

export default Wrapper;
```

#### ThemeToggle

components/ThemeToggle.jsx

```jsx
import { BsFillSunFill, BsFillMoonFill } from 'react-icons/bs';
import Wrapper from '../assets/wrappers/ThemeToggle';
import { useDashboardContext } from '../pages/DashboardLayout';

const ThemeToggle = () => {
  const { isDarkTheme, toggleDarkTheme } = useDashboardContext();
  return (
    <Wrapper onClick={toggleDarkTheme}>
      {isDarkTheme ? (
        <BsFillSunFill className='toggle-icon' />
      ) : (
        <BsFillMoonFill className='toggle-icon' />
      )}
    </Wrapper>
  );
};

export default ThemeToggle;
```

Navbar.jsx

```jsx
<div className='btn-container'>
  <ThemeToggle />
</div>
```

#### ThemeToggle CSS (optional)

assets/wrappers/ThemeToggle.js

```js
import styled from 'styled-components';

const Wrapper = styled.div`
  background: transparent;
  border-color: transparent;
  width: 3.5rem;
  height: 2rem;
  display: grid;
  place-items: center;
  cursor: pointer;

  .toggle-icon {
    font-size: 1.15rem;
    color: var(--text-color);
  }
`;
export default Wrapper;
```

#### Dark Theme - Logic

DashboardLayout.jsx

```jsx
const toggleDarkTheme = () => {
  const newDarkTheme = !isDarkTheme;
  setIsDarkTheme(newDarkTheme);
  document.body.classList.toggle('dark-theme', newDarkTheme);
  localStorage.setItem('darkTheme', newDarkTheme);
};
```

#### Access Theme

App.jsx

```jsx
const checkDefaultTheme = () => {
  const isDarkTheme =
    localStorage.getItem('darkTheme') === 'true'
  document.body.classList.toggle('dark-theme', isDarkTheme);
  return isDarkTheme;
};

const isDarkThemeEnabled = checkDefaultTheme();

{
path: 'dashboard',
element: <DashboardLayout isDarkThemeEnabled={isDarkThemeEnabled} />,
}
```

DashboardLayout.jsx

```jsx
const Dashboard = ({ isDarkThemeEnabled }) => {
  const [isDarkTheme, setIsDarkTheme] = useState(isDarkThemeEnabled);
};
```

#### Dark Theme CSS

index.css

```css
:root {
  /* DARK MODE */

  --dark-mode-bg-color: #333;
  --dark-mode-text-color: #f0f0f0;
  --dark-mode-bg-secondary-color: #3f3f3f;
  --dark-mode-text-secondary-color: var(--grey-300);

  --background-color: var(--grey-50);
  --text-color: var(--grey-900);
  --background-secondary-color: var(--white);
  --text-secondary-color: var(--grey-500);
}

.dark-theme {
  --text-color: var(--dark-mode-text-color);
  --background-color: var(--dark-mode-bg-color);
  --text-secondary-color: var(--dark-mode-text-secondary-color);
  --background-secondary-color: var(--dark-mode-bg-secondary-color);
}

body {
  background: var(--background-color);
  color: var(--text-color);
}
```

#### Folder Setup

- IMPORTANT !!!!
- remove existing .git folder (if any) from client

Mac

```sh
rm -rf .git
```

Windows

```sh
rmdir -Force -Recurse .git
```

```sh
rd /s /q .git
```

- Windows commands were shared by students and I have not personally tested them.
- git status should return :
  "fatal: Not a git repository (or any of the parent directories): .git"
- create jobify directory
- copy/paste client
- move README to root

#### Setup Server

- create package.json

```sh
npm init -y
```

- create and test server.js

```sh
node server
```

#### ES6 Modules

package.json

```json
  "type": "module",
```

Create test.js and implement named import

test.js

```js
export const value = 42;
```

server.js

```js
import { value } from './test.js';
console.log(value);
```

- don't forget about .js extension
- for named imports, names must match

#### Source Control

- create .gitignore
- copy values from client/.gitignore
- create Github Repo (optional)

#### Install Packages and Setup Install Script

```sh
npm install bcryptjs@2.4.3 concurrently@8.0.1 cookie-parser@1.4.6 dayjs@1.11.7 dotenv@16.0.3 express@4.18.2 express-async-errors@3.1.1 express-validator@7.0.1 http-status-codes@2.2.0 jsonwebtoken@9.0.0 mongoose@7.0.5 morgan@1.10.0 multer@1.4.5-lts.1 nanoid@4.0.2 nodemon@2.0.22 cloudinary@1.37.3 dayjs@1.11.9 datauri@4.1.0 helmet@7.0.0 express-rate-limit@6.8.0 express-mongo-sanitize@2.2.0

```

package.json

```json
"scripts": {
    "setup-project": "npm i && cd client && npm i"
  },
```

- install packages in root and client

```sh
npm run setup-project
```

#### Setup Basic Express

- install express and nodemon.
- setup a basic server which listening on PORT=5100
- create a basic home route which sends back "hello world"
- setup a script with nodemon package.

[Express Docs](https://expressjs.com/)

Express is a fast and minimalist web application framework for Node.js. It simplifies the process of building web applications by providing a robust set of features for handling HTTP requests, routing, middleware, and more. Express allows you to create server-side applications and APIs easily, with a focus on simplicity and flexibility.

[Nodemon Docs](https://nodemon.io/)

Nodemon is a development tool that improves the developer experience. It monitors your Node.js application for any changes in the code and automatically restarts the server whenever a change is detected. This eliminates the need to manually restart the server after every code modification, making the development process more efficient and productive. Nodemon is commonly used during development to save time and avoid the hassle of manual server restarts.

```sh
npm i express@4.18.2 nodemon@2.0.22
```

server.js

```js
import express from 'express';
const app = express();

app.get('/', (req, res) => {
  res.send('Hello World');
});

app.listen(5100, () => {
  console.log('server running....');
});
```

package.json

```json
"scripts": {
    "dev": "nodemon server.js"
  },
```

#### Thunder Client

Thunder Client is a popular Visual Studio Code extension that facilitates API testing and debugging. It provides a user-friendly interface for making HTTP requests and viewing the responses, allowing developers to easily test APIs, examine headers, and inspect JSON/XML payloads. Thunder Client offers features such as environment variables, request history, and the ability to save and organize requests for efficient development workflows.

[Thunder Client](https://www.thunderclient.com/)

- install and test home route

#### Accept JSON

Setup express middleware to accept json

server

```js
app.use(express.json());

app.post('/', (req, res) => {
  console.log(req);

  res.json({ message: 'Data received', data: req.body });
});
```

#### Morgan and Dotenv

[Morgan](https://www.npmjs.com/package/morgan)

HTTP request logger middleware for node.js

[Dotenv](https://www.npmjs.com/package/dotenv)

Dotenv is a zero-dependency module that loads environment variables from a .env file into process.env.

```sh
npm i morgan@1.10.0 dotenv@16.0.3
```

```js
import morgan from 'morgan';

app.use(morgan('dev'));
```

- create .env file in the root
- add PORT and NODE_ENV
- add .env to .gitignore

server.js

```js
import * as dotenv from 'dotenv';
dotenv.config();

if (process.env.NODE_ENV === 'development') {
  app.use(morgan('dev'));
}

const port = process.env.PORT || 5100;
app.listen(port, () => {
  console.log(`server running on PORT ${port}....`);
});
```

#### New Features

- fetch API
- global await (top-level await)
- watch mode

```js
try {
  const response = await fetch(
    'https://www.course-api.com/react-useReducer-cart-project'
  );
  const cartData = await response.json();
  console.log(cartData);
} catch (error) {
  console.log(error);
}
```

package.json

```json
 "scripts": {
    "watch": "node --watch server.js "
  },
```

#### Basic CRUD

- create jobs array where each item is an object with following properties
  id, company, position
- create routes to handle - create, read, update and delete functionalities

#### Get All Jobs

[Nanoid](https://www.npmjs.com/package/nanoid)

The nanoid package is a software library used for generating unique and compact identifiers in web applications or databases. It creates short and URL-safe IDs by combining random characters from a set of 64 characters. Nanoid is a popular choice due to its simplicity, efficiency, and collision-resistant nature.

```sh
npm i nanoid@4.0.2
```

server.js

```js
import { nanoid } from 'nanoid';

let jobs = [
  { id: nanoid(), company: 'apple', position: 'front-end' },
  { id: nanoid(), company: 'google', position: 'back-end' },
];

app.get('/api/v1/jobs', (req, res) => {
  res.status(200).json({ jobs });
});
```

#### Create, FindOne, Modify and Delete

```js
// CREATE JOB

app.post('/api/v1/jobs', (req, res) => {
  const { company, position } = req.body;
  if (!company || !position) {
    return res.status(400).json({ msg: 'please provide company and position' });
  }
  const id = nanoid(10);
  // console.log(id);
  const job = { id, company, position };
  jobs.push(job);
  res.status(200).json({ job });
});

// GET SINGLE JOB

app.get('/api/v1/jobs/:id', (req, res) => {
  const { id } = req.params;
  const job = jobs.find((job) => job.id === id);
  if (!job) {
    return res.status(404).json({ msg: `no job with id ${id}` });
  }
  res.status(200).json({ job });
});

// EDIT JOB

app.patch('/api/v1/jobs/:id', (req, res) => {
  const { company, position } = req.body;
  if (!company || !position) {
    return res.status(400).json({ msg: 'please provide company and position' });
  }
  const { id } = req.params;
  const job = jobs.find((job) => job.id === id);
  if (!job) {
    return res.status(404).json({ msg: `no job with id ${id}` });
  }

  job.company = company;
  job.position = position;
  res.status(200).json({ msg: 'job modified', job });
});

// DELETE JOB

app.delete('/api/v1/jobs/:id', (req, res) => {
  const { id } = req.params;
  const job = jobs.find((job) => job.id === id);
  if (!job) {
    return res.status(404).json({ msg: `no job with id ${id}` });
  }
  const newJobs = jobs.filter((job) => job.id !== id);
  jobs = newJobs;

  res.status(200).json({ msg: 'job deleted' });
});
```

#### Not Found Middleware

```js
app.use('*', (req, res) => {
  res.status(404).json({ msg: 'not found' });
});
```

#### Error Middleware

```js
app.use((err, req, res, next) => {
  console.log(err);
  res.status(500).json({ msg: 'something went wrong' });
});
```

#### Not Found and Error Middleware

The "not found" middleware in Express.js is used when a request is made to a route that does not exist. It catches these requests and responds with a 404 status code, indicating that the requested resource was not found.

On the other hand, the "error" middleware in Express.js is used to handle any errors that occur during the processing of a request. It is typically used to catch unexpected errors or exceptions that are not explicitly handled in the application code. It logs the error and sends a 500 status code, indicating an internal server error.

In summary, the "not found" middleware is specifically designed to handle requests for non-existent routes, while the "error" middleware is a catch-all for handling unexpected errors that occur during request processing.

- make a request to "/jobss"

```js
// GET ALL JOBS
app.get('/api/v1/jobs', (req, res) => {
  // console.log(jobss);
  res.status(200).json({ jobs });
});

// GET SINGLE JOB
app.get('/api/v1/jobs/:id', (req, res) => {
  const { id } = req.params;
  const job = jobs.find((job) => job.id === id);
  if (!job) {
    throw new Error('no job with that id');
    return res.status(404).json({ msg: `no job with id ${id}` });
  }
  res.status(200).json({ job });
});
```

#### Controller and Router

setup controllers and router

controllers/jobController.js

```js
import { nanoid } from 'nanoid';

let jobs = [
  { id: nanoid(), company: 'apple', position: 'front-end developer' },
  { id: nanoid(), company: 'google', position: 'back-end developer' },
];

export const getAllJobs = async (req, res) => {
  res.status(200).json({ jobs });
};

export const createJob = async (req, res) => {
  const { company, position } = req.body;

  if (!company || !position) {
    return res.status(400).json({ msg: 'please provide company and position' });
  }
  const id = nanoid(10);
  const job = { id, company, position };
  jobs.push(job);
  res.status(200).json({ job });
};

export const getJob = async (req, res) => {
  const { id } = req.params;
  const job = jobs.find((job) => job.id === id);
  if (!job) {
    // throw new Error('no job with that id');
    return res.status(404).json({ msg: `no job with id ${id}` });
  }
  res.status(200).json({ job });
};

export const updateJob = async (req, res) => {
  const { company, position } = req.body;
  if (!company || !position) {
    return res.status(400).json({ msg: 'please provide company and position' });
  }
  const { id } = req.params;
  const job = jobs.find((job) => job.id === id);
  if (!job) {
    return res.status(404).json({ msg: `no job with id ${id}` });
  }

  job.company = company;
  job.position = position;
  res.status(200).json({ msg: 'job modified', job });
};

export const deleteJob = async (req, res) => {
  const { id } = req.params;
  const job = jobs.find((job) => job.id === id);
  if (!job) {
    return res.status(404).json({ msg: `no job with id ${id}` });
  }
  const newJobs = jobs.filter((job) => job.id !== id);
  jobs = newJobs;

  res.status(200).json({ msg: 'job deleted' });
};
```

routes/jobRouter.js

```js
import { Router } from 'express';
const router = Router();

import {
  getAllJobs,
  getJob,
  createJob,
  updateJob,
  deleteJob,
} from '../controllers/jobController.js';

// router.get('/', getAllJobs);
// router.post('/', createJob);

router.route('/').get(getAllJobs).post(createJob);
router.route('/:id').get(getJob).patch(updateJob).delete(deleteJob);

export default router;
```

server.js

```js
import jobRouter from './routers/jobRouter.js';
app.use('/api/v1/jobs', jobRouter);
```

#### MongoDB

[MongoDb](https://www.mongodb.com/)

MongoDB is a popular NoSQL database that provides a flexible and scalable approach to storing and retrieving data. It uses a document-oriented model, where data is organized into collections of JSON-like documents. MongoDB offers high performance, horizontal scalability, and easy integration with modern development frameworks, making it suitable for handling diverse data types and handling large-scale applications.

MongoDB Atlas is a fully managed cloud database service provided by MongoDB, offering automated deployment, scaling, and monitoring of MongoDB clusters, allowing developers to focus on building their applications without worrying about infrastructure management.

#### Mongoosejs

[Mongoose](https://mongoosejs.com/)

Mongoose is an Object Data Modeling (ODM) library for Node.js that provides a straightforward and elegant way to interact with MongoDB. It allows developers to define schemas and models for their data, providing structure and validation. Mongoose also offers features like data querying, middleware, and support for data relationships, making it a powerful tool for building MongoDB-based applications.

```sh
npm i mongoose@7.0.5
```

server.js

```js
import mongoose from 'mongoose';

try {
  await mongoose.connect(process.env.MONGO_URL);
  app.listen(port, () => {
    console.log(`server running on PORT ${port}....`);
  });
} catch (error) {
  console.log(error);
  process.exit(1);
}
```

#### Job Model

models/JobModel.js

enum - data type represents a field with a predefined set of values

```js
import mongoose from 'mongoose';

const JobSchema = new mongoose.Schema(
  {
    company: String,
    position: String,
    jobStatus: {
      type: String,
      enum: ['interview', 'declined', 'pending'],
      default: 'pending',
    },
    jobType: {
      type: String,
      enum: ['full-time', 'part-time', 'internship'],
      default: 'full-time',
    },
    jobLocation: {
      type: String,
      default: 'my city',
    },
  },
  { timestamps: true }
);

export default mongoose.model('Job', JobSchema);
```

#### Create Job

jobController.js

```js
import Job from '../models/JobModel.js';

export const createJob = async (req, res) => {
  const { company, position } = req.body;
  const job = await Job.create({ company, position });
  res.status(201).json({ job });
};
```

#### Try / Catch

jobController.js

```js
export const createJob = async (req, res) => {
  const { company, position } = req.body;
  try {
    const job = await Job.create('something');
    res.status(201).json({ job });
  } catch (error) {
    res.status(500).json({ msg: 'server error' });
  }
};
```

#### express-async-errors

The "express-async-errors" package is an Express.js middleware that helps handle errors that occur within asynchronous functions. It catches unhandled errors inside async/await functions and forwards them to Express.js's error handling middleware, preventing the Node.js process from crashing. It simplifies error handling in Express.js applications by allowing you to write asynchronous code without worrying about manually catching and forwarding errors.

[Express Async Errors](https://www.npmjs.com/package/express-async-errors)

```sh
npm i express-async-errors@3.1.1
```

- setup import at the top !!!

  server.js

```js
import 'express-async-errors';
```

jobController.js

```js
export const createJob = async (req, res) => {
  const { company, position } = req.body;

  const job = await Job.create({ company, position });
  res.status(201).json({ job });
};
```

#### Get All Jobs

jobController.js

```js
export const getAllJobs = async (req, res) => {
  const jobs = await Job.find({});
  res.status(200).json({ jobs });
};
```

#### Get Single Job

```js
export const getJob = async (req, res) => {
  const { id } = req.params;
  const job = await Job.findById(id);
  if (!job) {
    return res.status(404).json({ msg: `no job with id ${id}` });
  }
  res.status(200).json({ job });
};
```

#### Delete Job

jobController.js

```js
export const deleteJob = async (req, res) => {
  const { id } = req.params;
  const removedJob = await Job.findByIdAndDelete(id);

  if (!removedJob) {
    return res.status(404).json({ msg: `no job with id ${id}` });
  }
  res.status(200).json({ job: removedJob });
};
```

#### Update Job

```js
export const updateJob = async (req, res) => {
  const { id } = req.params;

  const updatedJob = await Job.findByIdAndUpdate(id, req.body, {
    new: true,
  });

  if (!updatedJob) {
    return res.status(404).json({ msg: `no job with id ${id}` });
  }

  res.status(200).json({ job: updatedJob });
};
```

#### Status Codes

A library for HTTP status codes is useful because it provides a comprehensive and standardized set of codes that represent the outcome of HTTP requests. It allows developers to easily understand and handle different scenarios during web development, such as successful responses, client or server errors, redirects, and more. By using a status code library, developers can ensure consistent and reliable communication between servers and clients, leading to better error handling and improved user experience.

[Http Status Codes](https://www.npmjs.com/package/http-status-codes)

```sh
npm i http-status-codes@2.2.0

```

200 OK OK
201 CREATED Created

400 BAD_REQUEST Bad Request
401 UNAUTHORIZED Unauthorized

403 FORBIDDEN Forbidden
404 NOT_FOUND Not Found

500 INTERNAL_SERVER_ERROR Internal Server Error

- refactor 200 response in all controllers

jobController.js

```js
res.status(StatusCodes.OK).json({ jobs });
```

createJob

```js
res.status(StatusCodes.CREATED).json({ job });
```

#### Custom Error Class

jobController

```js
export const getJob = async (req, res) => {
  ....
  if (!job) {
    throw new Error('no job with that id');
    // return res.status(404).json({ msg: `no job with id ${id}` });
  }
  ...
};

```

errors/customErrors.js

```js
import { StatusCodes } from 'http-status-codes';
export class NotFoundError extends Error {
  constructor(message) {
    super(message);
    this.name = 'NotFoundError';
    this.statusCode = StatusCodes.NOT_FOUND;
  }
}
```

This code defines a custom error class NotFoundError that extends the built-in Error class in JavaScript. The NotFoundError class is designed to be used when a requested resource is not found, and it includes a status code of 404 to indicate this.

Here's a breakdown of the code:

class NotFoundError extends Error: This line defines a new class NotFoundError that extends the built-in Error class. This means that NotFoundError inherits all of the properties and methods of the Error class, and can also define its own properties and methods.

constructor(message): This is the constructor method for the NotFoundError class, which is called when a new instance of the class is created. The message parameter is the error message that will be displayed when the error is thrown.

super(message): This line calls the constructor of the Error class and passes the message parameter to it. This sets the error message for the NotFoundError instance.

this.name = "NotFoundError": This line sets the name property of the NotFoundError instance to "NotFoundError". This is a built-in property of the Error class that specifies the name of the error.

this.statusCode = 404: This line sets the statusCode property of the NotFoundError instance to 404. This is a custom property that is specific to the NotFoundError class and indicates the HTTP status code that should be returned when this error occurs.

By creating a custom error class like NotFoundError, you can provide more specific error messages and properties to help with debugging and error handling in your application.

#### Custom Error

jobController.js

```js
import { NotFoundError } from '../customErrors.js';

if (!job) throw new NotFoundError(`no job with id : ${id}`);
```

middleware/errorHandlerMiddleware.js

```js
import { StatusCodes } from 'http-status-codes';
const errorHandlerMiddleware = (err, req, res, next) => {
  console.log(err);
  const statusCode = err.statusCode || StatusCodes.INTERNAL_SERVER_ERROR;
  const msg = err.message || 'Something went wrong, try again later';

  res.status(statusCode).json({ msg });
};

export default errorHandlerMiddleware;
```

server.js

```js
import errorHandlerMiddleware from './middleware/errorHandlerMiddleware.js';

app.use(errorHandlerMiddleware);
```

#### Bad Request Error

400 BAD_REQUEST Bad Request
401 UNAUTHORIZED Unauthorized
403 FORBIDDEN Forbidden
404 NOT_FOUND Not Found

customErrors.js

```js
export class BadRequestError extends Error {
  constructor(message) {
    super(message);
    this.name = 'BadRequestError';
    this.statusCode = StatusCodes.BAD_REQUEST;
  }
}
export class UnauthenticatedError extends Error {
  constructor(message) {
    super(message);
    this.name = 'UnauthenticatedError';
    this.statusCode = StatusCodes.UNAUTHORIZED;
  }
}
export class UnauthorizedError extends Error {
  constructor(message) {
    super(message);
    this.name = 'UnauthorizedError';
    this.statusCode = StatusCodes.FORBIDDEN;
  }
}
```

#### Validation Layer

[Express Validator](https://express-validator.github.io/docs/)

```sh
npm i express-validator@7.0.1
```

#### Test Route

server.js

```js
app.post('/api/v1/test', (req, res) => {
  const { name } = req.body;
  res.json({ msg: `hello ${name}` });
});
```

#### Express Validator

```js
import { body, validationResult } from 'express-validator';

app.post(
  '/api/v1/test',
  [body('name').notEmpty().withMessage('name is required')],
  (req, res) => {
    const errors = validationResult(req);
    if (!errors.isEmpty()) {
      const errorMessages = errors.array().map((error) => error.msg);
      return res.status(400).json({ errors: errorMessages });
    }
    next();
  },
  (req, res) => {
    const { name } = req.body;
    res.json({ msg: `hello ${name}` });
  }
);
```

#### Validation Middleware

middleware/validationMiddleware.js

```js
import { body, validationResult } from 'express-validator';
import { BadRequestError } from '../errors/customErrors';
const withValidationErrors = (validateValues) => {
  return [
    validateValues,
    (req, res, next) => {
      const errors = validationResult(req);
      if (!errors.isEmpty()) {
        const errorMessages = errors.array().map((error) => error.msg);
        throw new BadRequestError(errorMessages);
      }
      next();
    },
  ];
};

export const validateTest = withValidationErrors([
  body('name')
    .notEmpty()
    .withMessage('name is required')
    .isLength({ min: 3, max: 50 })
    .withMessage('name must be between 3 and 50 characters long')
    .trim(),
]);
```

#### Remove Test Case From Server

#### Setup Constants

utils/constants.js

```js
export const JOB_STATUS = {
  PENDING: 'pending',
  INTERVIEW: 'interview',
  DECLINED: 'declined',
};

export const JOB_TYPE = {
  FULL_TIME: 'full-time',
  PART_TIME: 'part-time',
  INTERNSHIP: 'internship',
};

export const JOB_SORT_BY = {
  NEWEST_FIRST: 'newest',
  OLDEST_FIRST: 'oldest',
  ASCENDING: 'a-z',
  DESCENDING: 'z-a',
};
```

models/JobModel.js

```js
import mongoose from 'mongoose';
import { JOB_STATUS, JOB_TYPE } from '../utils/constants';
const JobSchema = new mongoose.Schema(
  {
    company: String,
    position: String,
    jobStatus: {
      type: String,
      enum: Object.values(JOB_STATUS),
      default: JOB_STATUS.PENDING,
    },
    jobType: {
      type: String,
      enum: Object.values(JOB_TYPE),
      default: JOB_TYPE.FULL_TIME,
    },
    jobLocation: {
      type: String,
      default: 'my city',
    },
  },
  { timestamps: true }
);
```

#### Validate Create Job

validationMiddleware.js

```js
import { JOB_STATUS, JOB_TYPE } from '../utils/constants.js';

export const validateJobInput = withValidationErrors([
  body('company').notEmpty().withMessage('company is required'),
  body('position').notEmpty().withMessage('position is required'),
  body('jobLocation').notEmpty().withMessage('job location is required'),
  body('jobStatus')
    .isIn(Object.values(JOB_STATUS))
    .withMessage('invalid status value'),
  body('jobType').isIn(Object.values(JOB_TYPE)).withMessage('invalid job type'),
]);
```

```js
import { validateJobInput } from '../middleware/validationMiddleware.js';

router.route('/').get(getAllJobs).post(validateJobInput, createJob);
router
  .route('/:id')
  .get(getJob)
  .patch(validateJobInput, updateJob)
  .delete(deleteJob);
```

- create job request

```json
{
  "company": "coding addict",
  "position": "backend-end",
  "jobStatus": "pending",
  "jobType": "full-time",
  "jobLocation": "florida"
}
```

#### Validate ID Parameter

validationMiddleware.js

```js
import mongoose from 'mongoose';

import { param } from 'express-validator';

export const validateIdParam = withValidationErrors([
  param('id')
    .custom((value) => mongoose.Types.ObjectId.isValid(value))
    .withMessage('invalid MongoDB id'),
]);
```

```js
export const validateIdParam = withValidationErrors([
  param('id').custom(async (value) => {
    const isValidId = mongoose.Types.ObjectId.isValid(value);
    if (!isValidId) throw new BadRequestError('invalid MongoDB id');
    const job = await Job.findById(value);
    if (!job) throw new NotFoundError(`no job with id : ${value}`);
  }),
]);
```

```js
import { body, param, validationResult } from 'express-validator';
import { BadRequestError, NotFoundError } from '../errors/customErrors.js';
import { JOB_STATUS, JOB_TYPE } from '../utils/constants.js';
import mongoose from 'mongoose';
import Job from '../models/JobModel.js';

const withValidationErrors = (validateValues) => {
  return [
    validateValues,
    (req, res, next) => {
      const errors = validationResult(req);
      if (!errors.isEmpty()) {
        const errorMessages = errors.array().map((error) => error.msg);
        if (errorMessages[0].startsWith('no job')) {
          throw new NotFoundError(errorMessages);
        }
        throw new BadRequestError(errorMessages);
      }
      next();
    },
  ];
};
```

- remove NotFoundError from getJob, updateJob, deleteJob controllers

#### Clean DB

#### User Model

models/UserModel.js

```js
import mongoose from 'mongoose';

const UserSchema = new mongoose.Schema({
  name: String,
  email: String,
  password: String,
  lastName: {
    type: String,
    default: 'lastName',
  },
  location: {
    type: String,
    default: 'my city',
  },
  role: {
    type: String,
    enum: ['user', 'admin'],
    default: 'user',
  },
});

export default mongoose.model('User', UserSchema);
```

#### User Controller and Router

controllers/authController.js

```js
export const register = async (req, res) => {
  res.send('register');
};
export const login = async (req, res) => {
  res.send('register');
};
```

routers/authRouter.js

```js
import { Router } from 'express';
import { register, login } from '../controllers/authController.js';
const router = Router();

router.post('/register', register);
router.post('/login', login);

export default router;
```

server.js

```js
import authRouter from './routers/authRouter.js';

app.use('/api/v1/auth', authRouter);
```

#### Create User - Initial Setup

authController.js

```js
import { StatusCodes } from 'http-status-codes';
import User from '../models/UserModel.js';

export const register = async (req, res) => {
  const user = await User.create(req.body);
  res.status(StatusCodes.CREATED).json({ user });
};
```

- register user request

```json
{
  "name": "john",
  "email": "john@gmail.com",
  "password": "secret123",
  "lastName": "smith",
  "location": "my city"
}
```

#### Validate User

validationMiddleware.js

```js
import User from '../models/UserModel.js';

export const validateRegisterInput = withValidationErrors([
  body('name').notEmpty().withMessage('name is required'),
  body('email')
    .notEmpty()
    .withMessage('email is required')
    .isEmail()
    .withMessage('invalid email format')
    .custom(async (email) => {
      const user = await User.findOne({ email });
      if (user) {
        throw new BadRequestError('email already exists');
      }
    }),
  body('password')
    .notEmpty()
    .withMessage('password is required')
    .isLength({ min: 8 })
    .withMessage('password must be at least 8 characters long'),
  body('location').notEmpty().withMessage('location is required'),
  body('lastName').notEmpty().withMessage('last name is required'),
]);
```

authRouter.js

```js
import { validateRegisterInput } from '../middleware/validationMiddleware.js';

router.post('/register', validateRegisterInput, register);
```

#### Admin Role

authController.js

```js
// first registered user is an admin
const isFirstAccount = (await User.countDocuments()) === 0;
req.body.role = isFirstAccount ? 'admin' : 'user';

const user = await User.create(req.body);
```

#### Hash Passwords

[bcryptjs](https://www.npmjs.com/package/bcryptjs)

```sh
npm i bcryptjs@2.4.3

```

authController.js

```js
import bcrypt from 'bcryptjs';

const register = async (req, res) => {
  // a random value that is added to the password before hashing
  const salt = await bcrypt.genSalt(10);
  const hashedPassword = await bcrypt.hash(req.body.password, salt);
  req.body.password = hashedPassword;

  const user = await User.create(req.body);
};
```

const salt = await bcrypt.genSalt(10);
This line generates a random "salt" value that will be used to hash the password. A salt is a random value that is added to the password before hashing, which helps to make the resulting hash more resistant to attacks like dictionary attacks and rainbow table attacks. The genSalt() function in bcrypt generates a random salt value using a specified "cost" value. The cost value determines how much CPU time is needed to calculate the hash, and higher cost values result in stronger hashes that are more resistant to attacks.

In this example, a cost value of 10 is used to generate the salt. This is a good default value that provides a good balance between security and performance. However, you may need to adjust the cost value based on the specific needs of your application.

const hashedPassword = await bcrypt.hash(password, salt);
This line uses the generated salt value to hash the password. The hash() function in bcrypt takes two arguments: the password to be hashed, and the salt value to use for the hash. It then calculates the hash value using a one-way hash function and the specified salt value.

The resulting hash value is a string that represents the hashed password. This string can then be stored in a database or other storage mechanism to be compared against the user's password when they log in.

By using a salt value and a one-way hash function, bcrypt helps to ensure that user passwords are stored securely and are resistant to attacks like password cracking and brute-force attacks.

##### BCRYPT VS BCRYPTJS

bcrypt and bcryptjs are both popular libraries for hashing passwords in Node.js applications. However, bcryptjs is considered to be a better choice for a few reasons:

Cross-platform compatibility: bcrypt is a native Node.js module that uses C++ bindings, which can make it difficult to install and use on some platforms. bcryptjs, on the other hand, is a pure JavaScript implementation that works on any platform.

Security: While both bcrypt and bcryptjs use the same underlying algorithm for hashing passwords, bcryptjs is designed to be more resistant to certain types of attacks, such as side-channel attacks.

Ease of use: bcryptjs has a simpler and more intuitive API than bcrypt, which can make it easier to use and integrate into your application.

Overall, while bcrypt and bcryptjs are both good choices for hashing passwords in Node.js applications, bcryptjs is considered to be a better choice for its cross-platform compatibility, improved security, ease of use, and ongoing maintenance.

#### Setup Password Utils

utils/passwordUtils.js

```js
import bcrypt from 'bcryptjs';

export async function hashPassword(password) {
  const salt = await bcrypt.genSalt(10);
  const hashedPassword = await bcrypt.hash(password, salt);
  return hashedPassword;
}
```

authController.js

```js
import { hashPassword } from '../utils/passwordUtils.js';

const register = async (req, res) => {
  const hashedPassword = await hashPassword(req.body.password);
  req.body.password = hashedPassword;

  const user = await User.create(req.body);
  res.status(StatusCodes.CREATED).json({ msg: 'user created' });
};
```

#### Login User

- login user request

```json
{
  "email": "john@gmail.com",
  "password": "secret123"
}
```

validationMiddleware.js

```js
export const validateLoginInput = withValidationErrors([
  body('email')
    .notEmpty()
    .withMessage('email is required')
    .isEmail()
    .withMessage('invalid email format'),
  body('password').notEmpty().withMessage('password is required'),
]);
```

authRouter.js

```js
import { validateLoginInput } from '../middleware/validationMiddleware.js';

router.post('/login', validateLoginInput, login);
```

#### Unauthenticated Error

authController.js

```js
import { UnauthenticatedError } from '../errors/customErrors.js';

const login = async (req, res) => {
  // check if user exists
  // check if password is correct

  const user = await User.findOne({ email: req.body.email });
  if (!user) throw new UnauthenticatedError('invalid credentials');

  res.send('login route');
};
```

#### Compare Password

passwordUtils.js

```js
export async function comparePassword(password, hashedPassword) {
  const isMatch = await bcrypt.compare(password, hashedPassword);
  return isMatch;
}
```

authController.js

```js
import { hashPassword, comparePassword } from '../utils/passwordUtils.js';

const login = async (req, res) => {
  // check if user exists
  // check if password is correct

  const user = await User.findOne({ email: req.body.email });

  if (!user) throw new UnauthenticatedError('invalid credentials');

  const isPasswordCorrect = await comparePassword(
    req.body.password,
    user.password
  );

  if (!isPasswordCorrect) throw new UnauthenticatedError('invalid credentials');
  res.send('login route');
};
```

Refactor

```js
const isValidUser = user && (await comparePassword(password, user.password));
if (!isValidUser) throw new UnauthenticatedError('invalid credentials');
```

#### JSON Web Token

A JSON Web Token (JWT) is a compact and secure way of transmitting data between parties. It is often used to authenticate and authorize users in web applications and APIs. JWTs contain information about the user and additional metadata, and can be used to securely transmit this information

[Useful Resource](https://jwt.io/introduction)

```sh
npm i jsonwebtoken@9.0.0
```

utils/tokenUtils.js

```js
import jwt from 'jsonwebtoken';

export const createJWT = (payload) => {
  const token = jwt.sign(payload, process.env.JWT_SECRET, {
    expiresIn: process.env.JWT_EXPIRES_IN,
  });
  return token;
};
```

JWT_SECRET represents the secret key used to sign the JWT. When creating a JWT, the payload (data) is signed with this secret key to generate a unique token. The secret key should be kept secure and should not be disclosed to unauthorized parties.

JWT_EXPIRES_IN specifies the expiration time for the JWT. It determines how long the token remains valid before it expires. The value of JWT_EXPIRES_IN is typically provided as a duration, such as "1h" for one hour or "7d" for seven days. Once the token expires, it is no longer considered valid and can't be used for authentication or authorization purposes.

These environment variables (JWT_SECRET and JWT_EXPIRES_IN) are read from the system environment during runtime, allowing for flexibility in configuration without modifying the code.

authController.js

```js
import { createJWT } from '../utils/tokenUtils.js';

const token = createJWT({ userId: user._id, role: user.role });
console.log(token);
```

#### Test JWT (optional)

[JWT](https://jwt.io/)

#### ENV Variables

- RESTART SERVER!!!!

.env

```js
JWT_SECRET=
JWT_EXPIRES_IN=
```

#### HTTP Only Cookie

An HTTP-only cookie is a cookie that can't be accessed by JavaScript running in the browser. It is designed to help prevent cross-site scripting (XSS) attacks, which can be used to steal cookies and other sensitive information.

##### HTTP Only Cookie VS Local Storage

An HTTP-only cookie is a type of cookie that is designed to be inaccessible to JavaScript running in the browser. It is primarily used for authentication purposes and is a more secure way of storing sensitive information like user tokens. Local storage, on the other hand, is a browser-based storage mechanism that is accessible to JavaScript, and is used to store application data like preferences or user-generated content. While local storage is convenient, it is not a secure way of storing sensitive information as it can be accessed and modified by JavaScript running in the browser.

authControllers.js

```js
const oneDay = 1000 * 60 * 60 * 24;

res.cookie('token', token, {
  httpOnly: true,
  expires: new Date(Date.now() + oneDay),
  secure: process.env.NODE_ENV === 'production',
});

res.status(StatusCodes.CREATED).json({ msg: 'user logged in' });
```

```js
const oneDay = 1000 * 60 * 60 * 24;
```

This line defines a constant oneDay that represents the number of milliseconds in a day. This value is used later to set the expiration time for the cookie.

```js
res.cookie('token', token, {...});:
```

This line sets a cookie with the name "token" and a value of token, which is the JWT that was generated for the user. The ... represents an object containing additional options for the cookie.

httpOnly: true: This option makes the cookie inaccessible to JavaScript running in the browser. This helps to prevent cross-site scripting (XSS) attacks, which can be used to steal cookies and other sensitive information.

expires: new Date(Date.now() + oneDay): This option sets the expiration time for the cookie. In this case, the cookie will expire one day from the current time (as represented by Date.now() + oneDay).

secure: process.env.NODE_ENV === 'production': This option determines whether the cookie should be marked as secure or not. If the NODE_ENV environment variable is set to "production", then the cookie is marked as secure, which means it can only be transmitted over HTTPS. This helps to prevent man-in-the-middle (MITM) attacks, which can intercept and modify cookies that are transmitted over unsecured connections.

jobsController.js

```js
export const getAllJobs = async (req, res) => {
  console.log(req);
  const jobs = await Job.find({});
  res.status(StatusCodes.OK).json({ jobs });
};
```

#### Clean DB

#### Connect User and Job

models/User.js

```js
const JobSchema = new mongoose.Schema(
  {
    ....
    createdBy: {
      type: mongoose.Types.ObjectId,
      ref: 'User',
    },
  },
  { timestamps: true }
);
```

#### Auth Middleware

middleware/authMiddleware.js

```js
export const authenticateUser = async (req, res, next) => {
  console.log('auth middleware');
  next();
};
```

server.js

```js
import { authenticateUser } from './middleware/authMiddleware.js';

app.use('/api/v1/jobs', authenticateUser, jobRouter);
```

##### Cookie Parser

[Cookie Parser](https://www.npmjs.com/package/cookie-parser)

```sh
npm i cookie-parser@1.4.6
```

server.js

```js
import cookieParser from 'cookie-parser';
app.use(cookieParser());
```

#### Access Token

authMiddleware.js

```js
import { UnauthenticatedError } from '../customErrors.js';

export const authenticateUser = async (req, res, next) => {
  const { token } = req.cookies;
  if (!token) {
    throw new UnauthenticatedError('authentication invalid');
  }
  next();
};
```

#### Verify Token

utils/tokenUtils.js

```js
export const verifyJWT = (token) => {
  const decoded = jwt.verify(token, process.env.JWT_SECRET);
  return decoded;
};
```

authMiddleware.js

```js
import { UnauthenticatedError } from '../customErrors.js';
import { verifyJWT } from '../utils/tokenUtils.js';

export const authenticateUser = async (req, res, next) => {
  const { token } = req.cookies;
  if (!token) {
    throw new UnauthenticatedError('authentication invalid');
  }

  try {
    const { userId, role } = verifyJWT(token);
    req.user = { userId, role };
    next();
  } catch (error) {
    throw new UnauthenticatedError('authentication invalid');
  }
};
```

jobController.js

```js
export const getAllJobs = async (req, res) => {
  console.log(req.user);
  const jobs = await Job.find({ createdBy: req.user.userId });
  res.status(StatusCodes.OK).json({ jobs });
};
```

#### Refactor Create Job

jobController.js

```js
export const createJob = async (req, res) => {
  req.body.createdBy = req.user.userId;
  const job = await Job.create(req.body);
  res.status(StatusCodes.CREATED).json({ job });
};
```

#### Check Permissions

validationMiddleware.js

```js
const withValidationErrors = (validateValues) => {
  return [
    validateValues,
    (req, res, next) => {
      const errors = validationResult(req);
      if (!errors.isEmpty()) {
       ...
        if (errorMessages[0].startsWith('not authorized')) {
          throw new UnauthorizedError('not authorized to access this route');
        }

        throw new BadRequestError(errorMessages);
      }
      next();
    },
  ];
};
```

```js
import {
  BadRequestError,
  NotFoundError,
  UnauthorizedError,
} from '../errors/customErrors.js';

export const validateIdParam = withValidationErrors([
  param('id').custom(async (value, { req }) => {
    const isValidMongoId = mongoose.Types.ObjectId.isValid(value);
    if (!isValidMongoId) throw new BadRequestError('invalid MongoDB id');
    const job = await Job.findById(value);
    if (!job) throw new NotFoundError(`no job with id ${value}`);
    const isAdmin = req.user.role === 'admin';
    const isOwner = req.user.userId === job.createdBy.toString();
    if (!isAdmin && !isOwner)
      throw UnauthorizedError('not authorized to access this route');
  }),
]);
```

#### Logout User

controllers/authController.js

```js
const logout = (req, res) => {
  res.cookie('token', 'logout', {
    httpOnly: true,
    expires: new Date(Date.now()),
  });
  res.status(StatusCodes.OK).json({ msg: 'user logged out!' });
};
```

routes/authRouter.js

```js
import { Router } from 'express';
const router = Router();
import { logout } from '../controllers/authController.js';

router.get('/logout', logout);

export default router;
```

#### User Routes

controllers/userController.js

```js
import { StatusCodes } from 'http-status-codes';
import User from '../models/User.js';
import Job from '../models/Job.js';

export const getCurrentUser = async (req, res) => {
  res.status(StatusCodes.OK).json({ msg: 'get current user' });
};

export const getApplicationStats = async (req, res) => {
  res.status(StatusCodes.OK).json({ msg: 'application stats' });
};

export const updateUser = async (req, res) => {
  res.status(StatusCodes.OK).json({ msg: 'update user' });
};
```

routes/userRouter.js

```js
import { Router } from 'express';
const router = Router();

import {
  getCurrentUser,
  getApplicationStats,
  updateUser,
} from '../controllers/userController.js';

router.get('/current-user', getCurrentUser);
router.get('/admin/app-stats', getApplicationStats);
router.patch('/update-user', updateUser);
export default router;
```

server.js

```js
import userRouter from './routers/userRouter.js';

app.use('/api/v1/users', authenticateUser, userRouter);
```

#### Get Current User

```js
export const getCurrentUser = async (req, res) => {
  const user = await User.findOne({ _id: req.user.userId });
  res.status(StatusCodes.OK).json({ user });
};
```

#### Remove Password

models/UserModel.js

```js
UserSchema.methods.toJSON = function () {
  var obj = this.toObject();
  delete obj.password;
  return obj;
};
```

```js
export const getCurrentUser = async (req, res) => {
  const user = await User.findOne({ _id: req.user.userId });
  const userWithoutPassword = user.toJSON();
  res.status(StatusCodes.OK).json({ user: userWithoutPassword });
};
```

#### Update User

middleware/validationMiddleware.js

```js
const validateUpdateUserInput = withValidationErrors([
  body('name').notEmpty().withMessage('name is required'),
  body('email')
    .notEmpty()
    .withMessage('email is required')
    .isEmail()
    .withMessage('invalid email format')
    .custom(async (email, { req }) => {
      const user = await User.findOne({ email });
      if (user && user._id.toString() !== req.user.userId) {
        throw new Error('email already exists');
      }
    }),
  body('lastName').notEmpty().withMessage('last name is required'),
  body('location').notEmpty().withMessage('location is required'),
]);
```

```js
export const updateUser = async (req, res) => {
  const updatedUser = await User.findByIdAndUpdate(req.user.userId, req.body);
  res.status(StatusCodes.OK).json({ msg: 'user updated' });
};
```

```json
{
  "name": "john",
  "email": "john@gmail.com",
  "lastName": "smith",
  "location": "florida"
}
```

#### Application Stats

```js
export const getApplicationStats = async (req, res) => {
  const users = await User.countDocuments();
  const jobs = await Job.countDocuments();
  res.status(StatusCodes.OK).json({ users, jobs });
};
```

```js
export const authorizePermissions = (...roles) => {
  return (req, res, next) => {
    if (!roles.includes(req.user.role)) {
      throw new UnauthorizedError('Unauthorized to access this route');
    }
    next();
  };
};
```

```js
import { authorizePermissions } from '../middleware/authMiddleware.js';

router.get('/admin/app-stats', [
  authorizePermissions('admin'),
  getApplicationStats,
]);
```

#### Setup Proxy

- only in dev env
- a must since cookies are sent back to the same server
- spin up both servers (our own and vite dev)

- server

```sh
npm run dev
```

- vite dev server

```sh
cd client && npm run dev
```

server.js

```js
app.get('/api/v1/test', (req, res) => {
  res.json({ msg: 'test route' });
});
```

client/src/main.jsx

```js
fetch('http://localhost:5100/api/v1/test')
  .then((res) => res.json())
  .then((data) => console.log(data));
```

client/vite.config.js

```js
export default defineConfig({
  plugins: [react()],
  server: {
    proxy: {
      '/api': {
        target: 'http://localhost:5100/api',
        changeOrigin: true,
        rewrite: (path) => path.replace(/^\/api/, ''),
      },
    },
  },
});
```

main.jsx

```js
fetch('/api/v1/test')
  .then((res) => res.json())
  .then((data) => console.log(data));
```

This code configures a proxy rule for the development server, specifically for requests that start with /api. Let's go through each property:

'/api': This is the path to match. If a request is made to the development server with a path that starts with /api, the proxy rule will be applied.
target: 'http://localhost:5100/api': This specifies the target URL where the requests will be redirected. In this case, any request that matches the /api path will be forwarded to http://localhost:5100/api.

changeOrigin: true: When set to true, this property changes the origin of the request to match the target URL. This can be useful when working with CORS (Cross-Origin Resource Sharing) restrictions.

rewrite: (path) => path.replace(/^\/api/, ''): This property allows you to modify the path of the request before it is forwarded to the target. In this case, the rewrite function uses a regular expression (/^\/api/) to remove the /api prefix from the path. For example, if a request is made to /api/users, the rewritten path will be /users.

To summarize, these lines of code configure a proxy rule for requests starting with /api on the development server. The requests will be redirected to http://localhost:5100/api, with the /api prefix removed from the path.

#### Concurrently

The concurrently npm package is a utility that allows you to run multiple commands concurrently in the same terminal window. It provides a convenient way to execute multiple tasks or processes simultaneously.

```sh
npm i concurrently@8.0.1
```

```json
"scripts": {
    "setup-project": "npm i && cd client && npm i",
    "server": "nodemon server",
    "client": "cd client && npm run dev",
    "dev": "concurrently --kill-others-on-fail \" npm run server\" \" npm run client\""
  },
```

By default, when a command fails, concurrently continues running the remaining commands. However, when --kill-others-on-fail is specified, if any of the commands fail, concurrently will immediately terminate all the other running commands.

#### Axios

Axios is a popular JavaScript library that simplifies the process of making HTTP requests from web browsers or Node.js. It provides a simple and elegant API for performing asynchronous HTTP requests, supporting features such as making GET, POST, PUT, and DELETE requests, handling request and response headers, handling request cancellation, and more.

[Axios Docs](https://axios-http.com/docs/intro)

```sh
npm i axios@1.3.6
```

main.jsx

```js
import axios from 'axios';

const data = await axios.get('/api/v1/test');
console.log(data);
```

#### Custom Instance

utils/customFetch.js

```js
import axios from 'axios';
const customFetch = axios.create({
  baseURL: '/api/v1',
});

export default customFetch;
```

main.jsx

```js
import customFetch from './utils/customFetch.js';

const data = await customFetch.get('/test');
console.log(data);
```

#### Typical Form Submission

```js
import { useState } from 'react';
import axios from 'axios';
const MyForm = () => {
  const [value, setValue] = useState('');

  const handleSubmit = async (event) => {
    event.preventDefault();
    const data = await axios.post('url', { value });
  };

  return <form onSubmit={handleSubmit}>.....</form>;
};

export default MyForm;
```

#### React Router - Action

Route actions are the "writes" to route loader "reads". They provide a way for apps to perform data mutations with simple HTML and HTTP semantics while React Router abstracts away the complexity of asynchronous UI and revalidation. This gives you the simple mental model of HTML + HTTP (where the browser handles the asynchrony and revalidation) with the behavior and UX capabilities of modern SPAs.

Register.jsx

```js
import { Form, redirect, useNavigation, Link } from 'react-router-dom';
import Wrapper from '../assets/wrappers/RegisterAndLoginPage';
import { FormRow, Logo } from '../components';

const Register = () => {
  return (
    <Wrapper>
      <Form method='post' className='form'>
        ...
      </Form>
    </Wrapper>
  );
};
export default Register;
```

App.jsx

```jsx
{
  path: 'register',
  element: <Register />,
  action: () => {
   console.log('hello there');
   return null;
    },
},
```

#### Register User

- FormData API

[FormData API - JS Nuggets](https://youtu.be/5-x4OUM-SP8)
[FormData API - React ](https://youtu.be/WrX5RndZIzw)

Register.jsx

```js
export const action = async ({ request }) => {
  const formData = await request.formData();
  const data = Object.fromEntries(formData);
  try {
    await customFetch.post('/auth/register', data);
    return redirect('/login');
  } catch (error) {
    return error;
  }
};
```

App.jsx

```jsx
import { action as registerAction } from './pages/Register';

{
  path: 'register',
  element: <Register />,
  action:registerAction
},
```

#### useNavigation() and navigation.state

This hook tells you everything you need to know about a page navigation to build pending navigation indicators and optimistic UI on data mutations. Things like:

- Global loading indicators
- Adding busy indicators to submit buttons

Navigation State

idle - There is no navigation pending.
submitting - A route action is being called due to a form submission using POST, PUT, PATCH, or DELETE
loading - The loaders for the next routes are being called to render the next page

Register.jsx

```js
const Register = () => {
  const navigation = useNavigation();
  const isSubmitting = navigation.state === 'submitting';
  return (
    <Wrapper>
      <Form method='post' className='form'>
        ....
        <button type='submit' className='btn btn-block' disabled={isSubmitting}>
          {isSubmitting ? 'submitting...' : 'submit'}
        </button>
        ...
      </Form>
    </Wrapper>
  );
};
export default Register;
```

#### React-Toastify

Import and set up the react-toastify library.

[React Toastify](https://fkhadra.github.io/react-toastify/introduction)

```sh
npm i react-toastify@9.1.2
```

main.jsx

```js
import 'react-toastify/dist/ReactToastify.css';
import { ToastContainer } from 'react-toastify';
ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
    <ToastContainer position='top-center' />
  </React.StrictMode>
);
```

Register.jsx

```js
import { toast } from 'react-toastify';

export const action = async ({ request }) => {
  const formData = await request.formData();
  const data = Object.fromEntries(formData);
  try {
    await customFetch.post('/auth/register', data);
    toast.success('Registration successful');
    return redirect('/login');
  } catch (error) {
    toast.error(error?.response?.data?.msg);
    return error;
  }
};
```

#### Login User

```js
import { Link, Form, redirect, useNavigation } from 'react-router-dom';
import Wrapper from '../assets/wrappers/RegisterAndLoginPage';
import { FormRow, Logo } from '../components';
import customFetch from '../utils/customFetch';
import { toast } from 'react-toastify';

export const action = async ({ request }) => {
  const formData = await request.formData();
  const data = Object.fromEntries(formData);
  try {
    await customFetch.post('/auth/login', data);
    toast.success('Login successful');
    return redirect('/dashboard');
  } catch (error) {
    toast.error(error?.response?.data?.msg);
    return error;
  }
};

const Login = () => {
  const navigation = useNavigation();
  const isSubmitting = navigation.state === 'submitting';
  return (
    <Wrapper>
      <Form method='post' className='form'>
        <Logo />
        <h4>login</h4>
        <FormRow type='email' name='email' defaultValue='john@gmail.com' />
        <FormRow type='password' name='password' defaultValue='secret123' />
        <button type='submit' className='btn btn-block' disabled={isSubmitting}>
          {isSubmitting ? 'submitting...' : 'submit'}
        </button>
        <button type='button' className='btn btn-block'>
          explore the app
        </button>
        <p>
          Not a member yet?
          <Link to='/register' className='member-btn'>
            Register
          </Link>
        </p>
      </Form>
    </Wrapper>
  );
};
export default Login;
```

#### Access Action Data (optional)

```js
import { useActionData } from 'react-router-dom';

export const action = async ({ request }) => {
  const formData = await request.formData();
  const data = Object.fromEntries(formData);
  const errors = { msg: '' };
  if (data.password.length < 3) {
    errors.msg = 'password too short';
    return errors;
  }
  try {
    await customFetch.post('/auth/login', data);
    toast.success('Login successful');
    return redirect('/dashboard');
  } catch (error) {
    // toast.error(error?.response?.data?.msg);
    errors.msg = error.response.data.msg;
    return errors;
  }
};

const Login = () => {
  const errors = useActionData();

  return (
    <Wrapper>
      <Form method='post' className='form'>
        ...
        {errors && <p style={{ color: 'red' }}>{errors.msg}</p>}
        ...
      </Form>
    </Wrapper>
  );
};
export default Login;
```

#### Get Current User

Each route can define a "loader" function to provide data to the route element before it renders.

- must return a value

DashboardLayout.jsx

```jsx
import { Outlet, redirect, useLoaderData } from 'react-router-dom';
import customFetch from '../utils/customFetch';

export const loader = async () => {
  try {
    const { data } = await customFetch('/users/current-user');
    return data;
  } catch (error) {
    return redirect('/');
  }
};


const DashboardLayout = ({ isDarkThemeEnabled }) => {
  const { user } = useLoaderData();

  return (
    <DashboardContext.Provider
      value={{
        user,
        showSidebar,
        isDarkTheme,
        toggleDarkTheme,
        toggleSidebar,
        logoutUser,
      }}
    >
      <Wrapper>
        <main className='dashboard'>
         ...
            <div className='dashboard-page'>
              <Outlet context={{ user }} />
            </div>
          </div>
        </main>
      </Wrapper>
    </DashboardContext.Provider>
  );
};
export const useDashboardContext = () => useContext(DashboardContext);
export default DashboardLayout;

```

#### Logout User

DashboardLayout.jsx

```js
import { useNavigate } from 'react-router-dom';
import { toast } from 'react-toastify';

const DashboardLayout = () => {
  const navigate = useNavigate();

  const logoutUser = async () => {
    navigate('/');
    await customFetch.get('/auth/logout');
    toast.success('Logging out...');
  };
};
```

#### AddJob - Structure

pages/AddJob.jsx

```js
import { FormRow } from '../components';
import Wrapper from '../assets/wrappers/DashboardFormPage';
import { useOutletContext } from 'react-router-dom';
import { JOB_STATUS, JOB_TYPE } from '../../../utils/constants';
import { Form, useNavigation, redirect } from 'react-router-dom';
import { toast } from 'react-toastify';
import customFetch from '../utils/customFetch';

const AddJob = () => {
  const { user } = useOutletContext();
  const navigation = useNavigation();
  const isSubmitting = navigation.state === 'submitting';

  return (
    <Wrapper>
      <Form method='post' className='form'>
        <h4 className='form-title'>add job</h4>
        <div className='form-center'>
          <FormRow type='text' name='position' />
          <FormRow type='text' name='company' />
          <FormRow
            type='text'
            labelText='job location'
            name='jobLocation'
            defaultValue={user.location}
          />

          <button
            type='submit'
            className='btn btn-block form-btn '
            disabled={isSubmitting}
          >
            {isSubmitting ? 'submitting...' : 'submit'}
          </button>
        </div>
      </Form>
    </Wrapper>
  );
};

export default AddJob;
```

#### Select Input

```js
<div className='form-row'>
  <label htmlFor='jobStatus' className='form-label'>
    job status
  </label>
  <select
    name='jobStatus'
    id='jobStatus'
    className='form-select'
    defaultValue={JOB_TYPE.FULL_TIME}
  >
    {Object.values(JOB_TYPE).map((itemValue) => {
      return (
        <option key={itemValue} value={itemValue}>
          {itemValue}
        </option>
      );
    })}
  </select>
</div>
```

#### FormRowSelect Component

components/FormRowSelect.jsx

```js
const FormRowSelect = ({ name, labelText, list, defaultValue = '' }) => {
  return (
    <div className='form-row'>
      <label htmlFor={name} className='form-label'>
        {labelText || name}
      </label>
      <select
        name={name}
        id={name}
        className='form-select'
        defaultValue={defaultValue}
      >
        {list.map((itemValue) => {
          return (
            <option key={itemValue} value={itemValue}>
              {itemValue}
            </option>
          );
        })}
      </select>
    </div>
  );
};
export default FormRowSelect;
```

pages/AddJob.jsx

```js
<FormRowSelect
  labelText='job status'
  name='jobStatus'
  defaultValue={JOB_STATUS.PENDING}
  list={Object.values(JOB_STATUS)}
  />
<FormRowSelect
  name='jobType'
  labelText='job type'
  defaultValue={JOB_TYPE.FULL_TIME}
  list={Object.values(JOB_TYPE)}
  />
```

#### Create Job

AddJob.jsx

```js
export const action = async ({ request }) => {
  const formData = await request.formData();
  const data = Object.fromEntries(formData);

  try {
    await customFetch.post('/jobs', data);
    toast.success('Job added successfully');
    return null;
  } catch (error) {
    toast.error(error?.response?.data?.msg);
    return error;
  }
};
```

#### Pending Class and Redirect

wrappers/BigSidebar.js

```css
.pending {
  background: var(--background-color);
}
```

AddJob.jsx

```js
export const action = async ({ request }) => {
  const formData = await request.formData();
  const data = Object.fromEntries(formData);

  try {
    await customFetch.post('/jobs', data);
    toast.success('Job added successfully');
    return redirect('all-jobs');
  } catch (error) {
    toast.error(error?.response?.data?.msg);
    return error;
  }
};
```

#### Add Job - CSS(optional)

wrappers/DashboardFormPage.js

```js
import styled from 'styled-components';

const Wrapper = styled.section`
  border-radius: var(--border-radius);
  width: 100%;
  background: var(--background-secondary-color);
  padding: 3rem 2rem 4rem;
  box-shadow: var(--shadow-2);
  .form-title {
    margin-bottom: 2rem;
  }

  .form {
    margin: 0;
    border-radius: 0;
    box-shadow: none;
    padding: 0;
    max-width: 100%;
    width: 100%;
  }
  .form-row {
    margin-bottom: 0;
  }
  .form-center {
    display: grid;
    row-gap: 1rem;
  }
  .form-btn {
    align-self: end;
    margin-top: 1rem;
    display: grid;
    place-items: center;
  }

  @media (min-width: 992px) {
    .form-center {
      grid-template-columns: 1fr 1fr;
      align-items: center;
      column-gap: 1rem;
    }
  }
  @media (min-width: 1120px) {
    .form-center {
      grid-template-columns: 1fr 1fr 1fr;
    }
  }
`;

export default Wrapper;
```

#### All Jobs - Structure

- create JobsContainer and SearchContainer (export)
- handle loader in App.jsx

```js
import { toast } from 'react-toastify';
import { JobsContainer, SearchContainer } from '../components';
import customFetch from '../utils/customFetch';
import { useLoaderData } from 'react-router-dom';
import { useContext, createContext } from 'react';

export const loader = async ({ request }) => {
  try {
    const { data } = await customFetch.get('/jobs');
    return {
      data,
    };
  } catch (error) {
    toast.error(error?.response?.data?.msg);
    return error;
  }
};

const AllJobs = () => {
  const { data } = useLoaderData();

  return (
    <>
      <SearchContainer />
      <JobsContainer />
    </>
  );
};
export default AllJobs;
```

#### Setup All Jobs Context

```js
const AllJobsContext = createContext();

const AllJobs = () => {
  const { data } = useLoaderData();

  return (
    <AllJobsContext.Provider value={{ data }}>
      <SearchContainer />
      <JobsContainer />
    </AllJobsContext.Provider>
  );
};

export const useAllJobsContext = () => useContext(AllJobsContext);
```

#### Render Jobs

- create Job.jsx

JobsContainer.jsx

```js
import Job from './Job';
import Wrapper from '../assets/wrappers/JobsContainer';

import { useAllJobsContext } from '../pages/AllJobs';

const JobsContainer = () => {
  const { data } = useAllJobsContext();
  const { jobs } = data;
  if (jobs.length === 0) {
    return (
      <Wrapper>
        <h2>No jobs to display...</h2>
      </Wrapper>
    );
  }

  return (
    <Wrapper>
      <div className='jobs'>
        {jobs.map((job) => {
          return <Job key={job._id} {...job} />;
        })}
      </div>
    </Wrapper>
  );
};

export default JobsContainer;
```

#### JobsContainer - CSS (optional)

wrappers/JobsContainer.js

```js
import styled from 'styled-components';

const Wrapper = styled.section`
  margin-top: 4rem;
  h2 {
    text-transform: none;
  }
  & > h5 {
    font-weight: 700;
    margin-bottom: 1.5rem;
  }
  .jobs {
    display: grid;
    grid-template-columns: 1fr;
    row-gap: 2rem;
  }
  @media (min-width: 1120px) {
    .jobs {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 2rem;
    }
  }
`;
export default Wrapper;
```

#### Dayjs

```sh
npm i dayjs@1.11.7
```

[Dayjs Docs](https://day.js.org/docs/en/installation/installation)

#### Job Component

- create JobInfo component

```js
import { FaLocationArrow, FaBriefcase, FaCalendarAlt } from 'react-icons/fa';
import { Link, Form } from 'react-router-dom';
import Wrapper from '../assets/wrappers/Job';
import JobInfo from './JobInfo';
import day from 'dayjs';
import advancedFormat from 'dayjs/plugin/advancedFormat';
day.extend(advancedFormat);

const Job = ({
  _id,
  position,
  company,
  jobLocation,
  jobType,
  createdAt,
  jobStatus,
}) => {
  const date = day(createdAt).format('MMM Do, YYYY');

  return (
    <Wrapper>
      <header>
        <div className='main-icon'>{company.charAt(0)}</div>
        <div className='info'>
          <h5>{position}</h5>
          <p>{company}</p>
        </div>
      </header>
      <div className='content'>
        <div className='content-center'>
          <JobInfo icon={<FaLocationArrow />} text={jobLocation} />
          <JobInfo icon={<FaCalendarAlt />} text={date} />
          <JobInfo icon={<FaBriefcase />} text={jobType} />
          <div className={`status ${jobStatus}`}>{jobStatus}</div>
        </div>

        <footer className='actions'>
          <Link className='btn edit-btn'>Edit</Link>
          <Form>
            <button type='submit' className='btn delete-btn'>
              Delete
            </button>
          </Form>
        </footer>
      </div>
    </Wrapper>
  );
};

export default Job;
```

#### JobInfo Component

```js
import Wrapper from '../assets/wrappers/JobInfo';

const JobInfo = ({ icon, text }) => {
  return (
    <Wrapper>
      <span className='job-icon'>{icon}</span>
      <span className='job-text'>{text}</span>
    </Wrapper>
  );
};

export default JobInfo;
```

#### JobInfo - CSS (optional)

wrappers/JobInfo.js

```js
import styled from 'styled-components';

const Wrapper = styled.div`
  display: flex;
  align-items: center;

  .job-icon {
    font-size: 1rem;
    margin-right: 1rem;
    display: flex;
    align-items: center;
    svg {
      color: var(--text-secondary-color);
    }
  }
  .job-text {
    text-transform: capitalize;
    letter-spacing: var(--letter-spacing);
  }
`;
export default Wrapper;
```

#### Job - CSS (optional)

```js
import styled from 'styled-components';

const Wrapper = styled.article`
  background: var(--background-secondary-color);
  border-radius: var(--border-radius);
  display: grid;
  grid-template-rows: 1fr auto;
  box-shadow: var(--shadow-2);

  header {
    padding: 1rem 1.5rem;
    border-bottom: 1px solid var(--grey-100);
    display: grid;
    grid-template-columns: auto 1fr;
    align-items: center;
  }
  .main-icon {
    width: 60px;
    height: 60px;
    display: grid;
    place-items: center;
    background: var(--primary-500);
    border-radius: var(--border-radius);
    font-size: 1.5rem;
    font-weight: 700;
    text-transform: uppercase;
    color: var(--white);
    margin-right: 2rem;
  }
  .info {
    h5 {
      margin-bottom: 0.5rem;
    }
    p {
      margin: 0;
      text-transform: capitalize;
      color: var(--text-secondary-color);
      letter-spacing: var(--letter-spacing);
    }
  }

  .content {
    padding: 1rem 1.5rem;
  }
  .content-center {
    display: grid;
    margin-top: 1rem;
    margin-bottom: 1.5rem;
    grid-template-columns: 1fr;
    row-gap: 1.5rem;
    align-items: center;
    @media (min-width: 576px) {
      grid-template-columns: 1fr 1fr;
    }
  }

  .status {
    border-radius: var(--border-radius);
    text-transform: capitalize;
    letter-spacing: var(--letter-spacing);
    text-align: center;
    width: 100px;
    height: 30px;
    display: grid;
    align-items: center;
  }
  .actions {
    margin-top: 1rem;
    display: flex;
    align-items: center;
  }
  .edit-btn,
  .delete-btn {
    height: 30px;
    font-size: 0.85rem;
    display: flex;
    align-items: center;
  }
  .edit-btn {
    margin-right: 0.5rem;
  }
`;

export default Wrapper;
```

#### Edit Job - Setup

Job.jsx

```js
<Link to={`../edit-job/${_id}`} className='btn edit-btn'>
  Edit
</Link>
```

pages/EditJob.jsx

```js
import { FormRow, FormRowSelect } from '../components';
import Wrapper from '../assets/wrappers/DashboardFormPage';
import { useLoaderData } from 'react-router-dom';
import { JOB_STATUS, JOB_TYPE } from '../../../utils/constants';
import { Form, useNavigation, redirect } from 'react-router-dom';
import { toast } from 'react-toastify';
import customFetch from '../utils/customFetch';

export const loader = async () => {
  return null;
};
export const action = async () => {
  return null;
};

const EditJob = () => {
  return <h1>EditJob Page</h1>;
};
export default EditJob;
```

- import EditJob page
  App.jsx

```js
import { loader as editJobLoader } from './pages/EditJob';
import { action as editJobAction } from './pages/EditJob';


{
  path: 'edit-job/:id',
  element: <EditJob />,
  loader: editJobLoader,
  action: editJobAction,
},
```

pages/EditJob.jsx

```js
export const loader = async ({ params }) => {
  try {
    const { data } = await customFetch.get(`/jobs/${params.id}`);
    return data;
  } catch (error) {
    toast.error(error.response.data.msg);
    return redirect('/dashboard/all-jobs');
  }
};
export const action = async () => {
  return null;
};

const EditJob = () => {
  const params = useParams();
  console.log(params);
  const { job } = useLoaderData();

  const navigation = useNavigation();
  const isSubmitting = navigation.state === 'submitting';
  return <h1>EditJob Page</h1>;
};
export default EditJob;
```

#### Edit Job - Complete

```js
export const action = async ({ request, params }) => {
  const formData = await request.formData();
  const data = Object.fromEntries(formData);

  try {
    await customFetch.patch(`/jobs/${params.id}`, data);
    toast.success('Job edited successfully');
    return redirect('/dashboard/all-jobs');
  } catch (error) {
    toast.error(error.response.data.msg);
    return error;
  }
};

const EditJob = () => {
  const { job } = useLoaderData();

  const navigation = useNavigation();
  const isSubmitting = navigation.state === 'submitting';

  return (
    <Wrapper>
      <Form method='post' className='form'>
        <h4 className='form-title'>edit job</h4>
        <div className='form-center'>
          <FormRow type='text' name='position' defaultValue={job.position} />
          <FormRow type='text' name='company' defaultValue={job.company} />
          <FormRow
            type='text'
            labelText='job location'
            name='jobLocation'
            defaultValue={job.jobLocation}
          />

          <FormRowSelect
            name='jobStatus'
            labelText='job status'
            defaultValue={job.jobStatus}
            list={Object.values(JOB_STATUS)}
          />
          <FormRowSelect
            name='jobType'
            labelText='job type'
            defaultValue={job.jobType}
            list={Object.values(JOB_TYPE)}
          />
          <button
            type='submit'
            className='btn btn-block form-btn '
            disabled={isSubmitting}
          >
            {isSubmitting ? 'submitting...' : 'submit'}
          </button>
        </div>
      </Form>
    </Wrapper>
  );
};

export default EditJob;
```

#### Delete Job

Job.jsx

```js
<Form method='post' action={`../delete-job/${_id}`}>
  <button type='submit' className='btn delete-btn'>
    Delete
  </button>
</Form>
```

pages/DeleteJob.jsx

```js
import { redirect } from 'react-router-dom';
import customFetch from '../utils/customFetch';
import { toast } from 'react-toastify';

export async function action({ params }) {
  try {
    await customFetch.delete(`/jobs/${params.id}`);
    toast.success('Job deleted successfully');
  } catch (error) {
    toast.error(error.response.data.msg);
  }
  return redirect('/dashboard/all-jobs');
}
```

App.jsx

```js
import { action as deleteJobAction } from './pages/DeleteJob';

 { path: 'delete-job/:id', action: deleteJobAction },
```

#### Admin Page

pages/Admin.jsx

```js
import { FaSuitcaseRolling, FaCalendarCheck } from 'react-icons/fa';

import { useLoaderData, redirect } from 'react-router-dom';
import customFetch from '../utils/customFetch';
import Wrapper from '../assets/wrappers/StatsContainer';
import { toast } from 'react-toastify';
export const loader = async () => {
  try {
    const response = await customFetch.get('/users/admin/app-stats');
    return response.data;
  } catch (error) {
    toast.error('You are not authorized to view this page');
    return redirect('/dashboard');
  }
};

const Admin = () => {
  const { users, jobs } = useLoaderData();

  return (
    <Wrapper>
      <h2>admin page</h2>
    </Wrapper>
  );
};
export default Admin;
```

App.jsx

```js
import { loader as adminLoader } from './pages/Admin';

{
  path: 'admin',
  element: <Admin />,
  loader: adminLoader,
},

```

NavLinks.jsx

```js
{
  links.map((link) => {
    const { text, path, icon } = link;
    const { role } = user;
    if (role !== 'admin' && path === 'admin') return;
  });
}
```

#### StatItem Component

- create StatItem.jsx
- import/export

  StatItem.jsx

```js
import Wrapper from '../assets/wrappers/StatItem';

const StatItem = ({ count, title, icon, color, bcg }) => {
  return (
    <Wrapper color={color} bcg={bcg}>
      <header>
        <span className='count'>{count}</span>
        <span className='icon'>{icon}</span>
      </header>
      <h5 className='title'>{title}</h5>
    </Wrapper>
  );
};

export default StatItem;
```

Admin.jsx

```js
import { StatItem } from '../components';

const Admin = () => {
  const { users, jobs } = useLoaderData();

  return (
    <Wrapper>
      <StatItem
        title='current users'
        count={users}
        color='#e9b949'
        bcg='#fcefc7'
        icon={<FaSuitcaseRolling />}
      />
      <StatItem
        title='total jobs'
        count={jobs}
        color='#647acb'
        bcg='#e0e8f9'
        icon={<FaCalendarCheck />}
      />
    </Wrapper>
  );
};
export default Admin;
```

#### Admin - CSS (optional)

wrappers/StatsContainer.js

```js
import styled from 'styled-components';

const Wrapper = styled.section`
  display: grid;
  row-gap: 2rem;
  @media (min-width: 768px) {
    grid-template-columns: 1fr 1fr;
    column-gap: 1rem;
  }
  @media (min-width: 1120px) {
    grid-template-columns: 1fr 1fr 1fr;
    column-gap: 1rem;
  }
`;
export default Wrapper;
```

wrappers/StatItem.js

```js
import styled from 'styled-components';

const Wrapper = styled.article`
  padding: 2rem;
  background: var(--background-secondary-color);
  border-radius: var(--border-radius);
  border-bottom: 5px solid ${(props) => props.color};
  header {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .count {
    display: block;
    font-weight: 700;
    font-size: 50px;
    color: ${(props) => props.color};
    line-height: 2;
  }
  .title {
    margin: 0;
    text-transform: capitalize;
    letter-spacing: var(--letter-spacing);
    text-align: left;
    margin-top: 0.5rem;
    font-size: 1.25rem;
  }
  .icon {
    width: 70px;
    height: 60px;
    background: ${(props) => props.bcg};
    border-radius: var(--border-radius);
    display: flex;
    align-items: center;
    justify-content: center;
    svg {
      font-size: 2rem;
      color: ${(props) => props.color};
    }
  }
`;

export default Wrapper;
```

#### Avatar Image

- get two images from pexels

[pexels](https://www.pexels.com/search/person/)

#### Setup Public Folder

server.js

```js
import { dirname } from 'path';
import { fileURLToPath } from 'url';
import path from 'path';

const __dirname = dirname(fileURLToPath(import.meta.url));

app.use(express.static(path.resolve(__dirname, './public')));
```

- http://localhost:5100/imageName

#### Profile Page - Initial Setup

- remove jobs,users from DB
- add avatar property in the user model

models/UserModel.js

```js
const UserSchema = new mongoose.Schema({
  avatar: String,
  avatarPublicId: String,
});
```

#### Profile Page - Structure

pages/Profile.jsx

```js
import { FormRow } from '../components';
import Wrapper from '../assets/wrappers/DashboardFormPage';
import { useOutletContext } from 'react-router-dom';
import { useNavigation, Form } from 'react-router-dom';
import customFetch from '../utils/customFetch';
import { toast } from 'react-toastify';

const Profile = () => {
  const { user } = useOutletContext();
  const { name, lastName, email, location } = user;
  const navigation = useNavigation();
  const isSubmitting = navigation.state === 'submitting';
  return (
    <Wrapper>
      <Form method='post' className='form' encType='multipart/form-data'>
        <h4 className='form-title'>profile</h4>

        <div className='form-center'>
          <div className='form-row'>
            <label htmlFor='image' className='form-label'>
              Select an image file (max 0.5 MB):
            </label>
            <input
              type='file'
              id='avatar'
              name='avatar'
              className='form-input'
              accept='image/*'
            />
          </div>
          <FormRow type='text' name='name' defaultValue={name} />
          <FormRow
            type='text'
            labelText='last name'
            name='lastName'
            defaultValue={lastName}
          />
          <FormRow type='email' name='email' defaultValue={email} />
          <FormRow type='text' name='location' defaultValue={location} />
          <button
            className='btn btn-block form-btn'
            type='submit'
            disabled={isSubmitting}
          >
            {isSubmitting ? 'submitting...' : 'save changes'}
          </button>
        </div>
      </Form>
    </Wrapper>
  );
};

export default Profile;
```

#### Profile Page - Action

- import/export action (App.jsx)

```js
export const action = async ({ request }) => {
  const formData = await request.formData();

  const file = formData.get('avatar');
  if (file && file.size > 500000) {
    toast.error('Image size too large');
    return null;
  }

  try {
    await customFetch.patch('/users/update-user', formData);
    toast.success('Profile updated successfully');
  } catch (error) {
    toast.error(error?.response?.data?.msg);
  }
  return null;
};
```

#### Update User - Server

```sh
npm i multer@1.4.5
```

Multer is a popular middleware package for handling multipart/form-data in Node.js web applications. It is commonly used for handling file uploads. Multer simplifies the process of accepting and storing files submitted through HTTP requests by providing an easy-to-use API. It integrates seamlessly with Express.js and allows developers to define upload destinations, file size limits, and other configurations.

- create middleware/multerMiddleware.js
- setup multer

```js
import multer from 'multer';

const storage = multer.diskStorage({
  destination: (req, file, cb) => {
    // set the directory where uploaded files will be stored
    cb(null, 'public/uploads');
  },
  filename: (req, file, cb) => {
    const fileName = file.originalname;
    // set the name of the uploaded file
    cb(null, fileName);
  },
});
const upload = multer({ storage });

export default upload;
```

routes/userRouter.js

```js
import upload from '../middleware/multerMiddleware.js';

router.patch(
  '/update-user',
  upload.single('avatar'),
  validateUpdateUserInput,
  updateUser
);
```

First, the multer package is imported.

Then, a storage object is created using multer.diskStorage(). This object specifies the configuration for storing uploaded files. In this case, the destination function determines the directory where the uploaded files will be saved, which is set to 'public/uploads'. The filename function defines the name of the uploaded file, which is set to the original filename.

Next, a multer middleware is created by passing the storage object as a configuration option. This multer middleware will be used to handle file uploads in the application.

In this case, upload is an instance of the Multer middleware that was created earlier. The .single() method is called on this instance to indicate that only one file will be uploaded. The argument 'avatar' specifies the name of the field in the HTTP request that corresponds to the uploaded file.

When this middleware is used in an HTTP route handler, it will process the incoming request and extract the file attached to the 'avatar' field. Multer will then save the file according to the specified storage configuration, which includes the destination directory and filename logic defined earlier. The uploaded file can be accessed in the route handler using req.file.

#### Cloudinary - Create Account/Get API Keys

[Cloudinary](https://cloudinary.com/)

Cloudinary is a cloud-based media management platform that helps businesses store, optimize, and deliver images and videos across the web. It provides developers with an easy way to upload, manipulate, and serve media assets, enabling faster and more efficient delivery of visual content on websites and applications. Cloudinary also offers features like automatic resizing, format conversion, and responsive delivery to ensure optimal user experiences across different devices and network conditions.

.env

```sh
CLOUD_NAME=
CLOUD_API_KEY=
CLOUD_API_SECRET=
```

#### Cloudinary - Setup Instance

```sh
npm i cloudinary@1.37.3
```

server

```js
import cloudinary from 'cloudinary';

cloudinary.config({
  cloud_name: process.env.CLOUD_NAME,
  api_key: process.env.CLOUD_API_KEY,
  api_secret: process.env.CLOUD_API_SECRET,
});
```

#### Update User Controller

controllers/userController.js

```js
import cloudinary from 'cloudinary';
import { promises as fs } from 'fs';

export const updateUser = async (req, res) => {
  const newUser = { ...req.body };
  delete newUser.password;
  if (req.file) {
    const response = await cloudinary.v2.uploader.upload(req.file.path);
    await fs.unlink(req.file.path);
    newUser.avatar = response.secure_url;
    newUser.avatarPublicId = response.public_id;
  }

  const updatedUser = await User.findByIdAndUpdate(req.user.userId, newUser);

  if (req.file && updatedUser.avatarPublicId) {
    await cloudinary.v2.uploader.destroy(updatedUser.avatarPublicId);
  }
  res.status(StatusCodes.OK).json({ msg: 'update user' });
};
```

#### Logout Container

```js
{
  user.avatar ? (
    <img src={user.avatar} alt='avatar' className='img' />
  ) : (
    <FaUserCircle />
  );
}
```

#### Submit Btn Component

- create component SubmitBtn (export/import)
- add all classes, including'.form-btn'
- setup in Register,Login, AddJob, EditJob, Profile
- make sure to add formBtn prop

```js
import { useNavigation } from 'react-router-dom';
const SubmitBtn = ({ formBtn }) => {
  const navigation = useNavigation();
  const isSubmitting = navigation.state === 'submitting';
  return (
    <button
      type='submit'
      className={`btn btn-block ${formBtn && 'form-btn'}`}
      disabled={isSubmitting}
    >
      {isSubmitting ? 'submitting...' : 'submit'}
    </button>
  );
};
export default SubmitBtn;
```

#### Test User

- create test user
- feel free to use one of the chatGPT options

```json
{
  "name": "Zippy",
  "email": "test@test.com",
  "password": "secret123",
  "lastName": "ShakeAndBake",
  "location": "Codeville"
}
{
  "name": "Chuckleberry",
  "email": "test@test.com",
  "password": "secret123",
  "lastName": "Gigglepants",
  "location": "Laughterland"
}

{
  "name": "Bubbles McLaughster",
  "email": "test@test.com",
  "password": "secret123",
  "lastName": "Ticklebottom",
  "location": "Giggle City"
}


{
  "name": "Gigglesworth",
  "email": "test@test.com",
  "password": "secret123",
  "lastName": "Snickerdoodle",
  "location": "Chuckleburg"
}
```

#### Test User - Login Page

```js
import { useNavigate } from 'react-router-dom';

const Login = () => {
  const navigate = useNavigate();
  const loginDemoUser = async () => {
    const data = {
      email: 'test@test.com',
      password: 'secret123',
    };
    try {
      await customFetch.post('/auth/login', data);
      toast.success('take a test drive');
      navigate('/dashboard');
    } catch (error) {
      toast.error(error?.response?.data?.msg);
    }
  };
  return (
    <Wrapper>
      ...
        <button type='button' className='btn btn-block' onClick={loginDemoUser}>
          explore the app
        </button>
        ...
      </Form>
    </Wrapper>
  );
};
export default Login;
```

#### Test User - Restrict Access

authMiddleware

```js
import {
  BadRequestError,
} from '../errors/customErrors.js';

export const authenticateUser = (req, res, next) => {
  ...
  try {
    const { userId, role } = verifyJWT(token);
    const testUser = userId === 'testUserId';
    req.user = { userId, role, testUser };
    next();
  }
  ....
};

export const checkForTestUser = (req, res, next) => {
  if (req.user.testUser) {
    throw new BadRequestError('Demo User. Read Only!');
  }
  next();
};

```

- add to updateUser, createJob, updateJob, deleteJob

#### Mock Data

[Mockaroo ](https://www.mockaroo.com/)

```json
{
  "company": "Cogidoo",
  "position": "Help Desk Technician",
  "jobLocation": "Vyksa",
  "jobStatus": "pending",
  "jobType": "part-time",
  "createdAt": "2022-07-25T21:26:23Z"
}
```

- rename and save json in utils

#### Populate DB

- create populate.js
- setup for test user and admin

```js
import { readFile } from 'fs/promises';
import mongoose from 'mongoose';
import dotenv from 'dotenv';
dotenv.config();

import Job from './models/JobModel.js';
import User from './models/UserModel.js';
try {
  await mongoose.connect(process.env.MONGO_URL);
  // const user = await User.findOne({ email: 'john@gmail.com' });
  const user = await User.findOne({ email: 'test@test.com' });

  const jsonJobs = JSON.parse(
    await readFile(new URL('./utils/mockData.json', import.meta.url))
  );
  const jobs = jsonJobs.map((job) => {
    return { ...job, createdBy: user._id };
  });
  await Job.deleteMany({ createdBy: user._id });
  await Job.create(jobs);
  console.log('Success!!!');
  process.exit(0);
} catch (error) {
  console.log(error);
  process.exit(1);
}
```

#### Stats - Setup

- create controller
- setup route and thunder client
- install/setup dayjs on the server

jobController.js

```js
import mongoose from 'mongoose';
import day from 'dayjs';

export const showStats = async (req, res) => {
  const defaultStats = {
    pending: 22,
    interview: 11,
    declined: 4,
  };

  let monthlyApplications = [
    {
      date: 'May 23',
      count: 12,
    },
    {
      date: 'Jun 23',
      count: 9,
    },
    {
      date: 'Jul 23',
      count: 3,
    },
  ];
  res.status(StatusCodes.OK).json({ defaultStats, monthlyApplications });
};
```

#### Stats - Complete Server Functionality

[MongoDB Docs](https://www.mongodb.com/docs/manual/core/aggregation-pipeline/)

The MongoDB aggregation pipeline is like a factory line for data. Data enters, it goes through different stages like cleaning, sorting, or grouping, and comes out at the end changed in some way. It's a way to process data inside MongoDB.

jobController.js

```js
export const showStats = async (req, res) => {
  let stats = await Job.aggregate([
    { $match: { createdBy: new mongoose.Types.ObjectId(req.user.userId) } },
    { $group: { _id: '$jobStatus', count: { $sum: 1 } } },
  ]);
  stats = stats.reduce((acc, curr) => {
    const { _id: title, count } = curr;
    acc[title] = count;
    return acc;
  }, {});

  const defaultStats = {
    pending: stats.pending || 0,
    interview: stats.interview || 0,
    declined: stats.declined || 0,
  };

  let monthlyApplications = await Job.aggregate([
    { $match: { createdBy: new mongoose.Types.ObjectId(req.user.userId) } },
    {
      $group: {
        _id: { year: { $year: '$createdAt' }, month: { $month: '$createdAt' } },
        count: { $sum: 1 },
      },
    },
    { $sort: { '_id.year': -1, '_id.month': -1 } },
    { $limit: 6 },
  ]);
  monthlyApplications = monthlyApplications
    .map((item) => {
      const {
        _id: { year, month },
        count,
      } = item;

      const date = day()
        .month(month - 1)
        .year(year)
        .format('MMM YY');
      return { date, count };
    })
    .reverse();

  res.status(StatusCodes.OK).json({ defaultStats, monthlyApplications });
};
```

#### Commentary

```js
let stats = await Job.aggregate([
  { $match: { createdBy: new mongoose.Types.ObjectId(req.user.userId) } },
  { $group: { _id: '$jobStatus', count: { $sum: 1 } } },
]);
```

let stats = await Job.aggregate([ ... ]); This line says we're going to perform an aggregation operation on the Job collection in MongoDB and save the result in a variable called stats. The await keyword is used to wait for the operation to finish before continuing, as the operation is asynchronous (i.e., it runs in the background).

{ $match: { createdBy: new mongoose.Types.ObjectId(req.user.userId) } } This is the first stage of the pipeline. It filters the jobs so that only the ones created by the user specified by req.user.userId are passed to the next stage. The new mongoose.Types.ObjectId(req.user.userId) part converts req.user.userId into an ObjectId (which is the format MongoDB uses for ids).

{ $group: { _id: '$jobStatus', count: { $sum: 1 } } } This is the second stage of the pipeline. It groups the remaining jobs by their status (the jobStatus field). For each group, it calculates the count of jobs by adding 1 for each job ({ $sum: 1 }), and stores this in a field called count.

```js
let monthlyApplications = await Job.aggregate([
  { $match: { createdBy: new mongoose.Types.ObjectId(req.user.userId) } },
  {
    $group: {
      _id: { year: { $year: '$createdAt' }, month: { $month: '$createdAt' } },
      count: { $sum: 1 },
    },
  },
  { $sort: { '_id.year': -1, '_id.month': -1 } },
  { $limit: 6 },
]);
```

let monthlyApplications = await Job.aggregate([ ... ]); This line indicates that an aggregation operation will be performed on the Job collection in MongoDB. The result will be stored in the variable monthlyApplications. The await keyword ensures that the code waits for this operation to complete before proceeding, as it is an asynchronous operation.

{ $match: { createdBy: new mongoose.Types.ObjectId(req.user.userId) } } This is the first stage of the pipeline. It filters the jobs to only those created by the user identified by req.user.userId.

{ $group: { _id: { year: { $year: '$createdAt' }, month: { $month: '$createdAt' } }, count: { $sum: 1 } } } This is the second stage of the pipeline. It groups the remaining jobs based on the year and month when they were created. For each group, it calculates the count of jobs by adding 1 for each job in the group.

{ $sort: { '\_id.year': -1, '\_id.month': -1 } } This is the third stage of the pipeline. It sorts the groups by year and month in descending order. The -1 indicates descending order. So it starts with the most recent year and month.

{ $limit: 6 } This is the fourth and last stage of the pipeline. It limits the output to the top 6 groups, after sorting. This is effectively getting the job count for the last 6 months.

So, monthlyApplications will be an array with up to 6 elements, each representing the number of jobs created by the user in a specific month and year. The array will be sorted by year and month, starting with the most recent.

#### Stats - Front-End Setup

- create four components
- StatsContainer and ChartsContainer (import/export)
- AreaChart, BarChart (local)

pages/Stats.jsx

```js
import { ChartsContainer, StatsContainer } from '../components';
import customFetch from '../utils/customFetch';
import { useLoaderData } from 'react-router-dom';
export const loader = async () => {
  try {
    const response = await customFetch.get('/jobs/stats');
    return response.data;
  } catch (error) {
    return error;
  }
};

const Stats = () => {
  const { defaultStats, monthlyApplications } = useLoaderData();
  return (
    <>
      <StatsContainer defaultStats={defaultStats} />
      {monthlyApplications?.length > 0 && (
        <ChartsContainer data={monthlyApplications} />
      )}
    </>
  );
};
export default Stats;
```

#### Stats Container

```js
import { FaSuitcaseRolling, FaCalendarCheck, FaBug } from 'react-icons/fa';
import Wrapper from '../assets/wrappers/StatsContainer';
import StatItem from './StatItem';
const StatsContainer = ({ defaultStats }) => {
  const stats = [
    {
      title: 'pending applications',
      count: defaultStats?.pending || 0,
      icon: <FaSuitcaseRolling />,
      color: '#f59e0b',
      bcg: '#fef3c7',
    },
    {
      title: 'interviews scheduled',
      count: defaultStats?.interview || 0,
      icon: <FaCalendarCheck />,
      color: '#647acb',
      bcg: '#e0e8f9',
    },
    {
      title: 'jobs declined',
      count: defaultStats?.declined || 0,
      icon: <FaBug />,
      color: '#d66a6a',
      bcg: '#ffeeee',
    },
  ];
  return (
    <Wrapper>
      {stats.map((item) => {
        return <StatItem key={item.title} {...item} />;
      })}
    </Wrapper>
  );
};
export default StatsContainer;
```

#### ChartsContainer

```js
import { useState } from 'react';

import BarChart from './BarChart';
import AreaChart from './AreaChart';
import Wrapper from '../assets/wrappers/ChartsContainer';

const ChartsContainer = ({ data }) => {
  const [barChart, setBarChart] = useState(true);

  return (
    <Wrapper>
      <h4>Monthly Applications</h4>
      <button type='button' onClick={() => setBarChart(!barChart)}>
        {barChart ? 'Area Chart' : 'Bar Chart'}
      </button>
      {barChart ? <BarChart data={data} /> : <AreaChart data={data} />}
    </Wrapper>
  );
};

export default ChartsContainer;
```

#### Charts

[recharts](https://recharts.org/en-US/)

- in the client

```sh
npm i recharts@2.5.0
```

#### Area Chart

```js
import {
  ResponsiveContainer,
  AreaChart,
  Area,
  XAxis,
  YAxis,
  CartesianGrid,
  Tooltip,
} from 'recharts';

const AreaChartComponent = ({ data }) => {
  return (
    <ResponsiveContainer width='100%' height={300}>
      <AreaChart data={data} margin={{ top: 50 }}>
        <CartesianGrid strokeDasharray='3 3' />
        <XAxis dataKey='date' />
        <YAxis allowDecimals={false} />
        <Tooltip />
        <Area type='monotone' dataKey='count' stroke='#2cb1bc' fill='#bef8fd' />
      </AreaChart>
    </ResponsiveContainer>
  );
};

export default AreaChartComponent;
```

#### Bar Chart

```js
import {
  BarChart,
  Bar,
  XAxis,
  YAxis,
  CartesianGrid,
  Tooltip,
  ResponsiveContainer,
} from 'recharts';

const BarChartComponent = ({ data }) => {
  return (
    <ResponsiveContainer width='100%' height={300}>
      <BarChart data={data} margin={{ top: 50 }}>
        <CartesianGrid strokeDasharray='3 3 ' />
        <XAxis dataKey='date' />
        <YAxis allowDecimals={false} />
        <Tooltip />
        <Bar dataKey='count' fill='#2cb1bc' barSize={75} />
      </BarChart>
    </ResponsiveContainer>
  );
};

export default BarChartComponent;
```

#### Charts CSS (optional)

wrappers/ChartsContainer.js

```js
import styled from 'styled-components';

const Wrapper = styled.section`
  margin-top: 4rem;
  text-align: center;
  button {
    background: transparent;
    border-color: transparent;
    text-transform: capitalize;
    color: var(--primary-500);
    font-size: 1.25rem;
    cursor: pointer;
  }
  h4 {
    text-align: center;
    margin-bottom: 0.75rem;
  }
`;

export default Wrapper;
```

#### Get All Jobs - Server

jobController.js

Query parameters, also known as query strings or URL parameters, are used to pass information to a web server through the URL of a webpage. They are typically appended to the end of a URL after a question mark (?) and separated by ampersands (&). Query parameters consist of a key-value pair, where the key represents the parameter name and the value represents the corresponding data being passed. They are commonly used in web applications to provide additional context or parameters for server-side processing or to filter and sort data.

```js
export const getAllJobs = async (req, res) => {
  const { search, jobStatus, jobType, sort } = req.query;

  const queryObject = {
    createdBy: req.user.userId,
  };

  if (search) {
    queryObject.$or = [
      { position: { $regex: search, $options: 'i' } },
      { company: { $regex: search, $options: 'i' } },
    ];
  }
  if (jobStatus && jobStatus !== 'all') {
    queryObject.jobStatus = jobStatus;
  }
  if (jobType && jobType !== 'all') {
    queryObject.jobType = jobType;
  }

  const sortOptions = {
    newest: '-createdAt',
    oldest: 'createdAt',
    'a-z': 'position',
    'z-a': '-position',
  };

  const sortKey = sortOptions[sort] || sortOptions.newest;

  // setup pagination
  const page = Number(req.query.page) || 1;
  const limit = Number(req.query.limit) || 10;
  const skip = (page - 1) * limit;

  const jobs = await Job.find(queryObject)
    .sort(sortKey)
    .skip(skip)
    .limit(limit);

  const totalJobs = await Job.countDocuments(queryObject);
  const numOfPages = Math.ceil(totalJobs / limit);

  res
    .status(StatusCodes.OK)
    .json({ totalJobs, numOfPages, currentPage: page, jobs });
};
```

#### Search Container

- setup log in AllJobs loader

```js
import { FormRow, FormRowSelect, SubmitBtn } from '.';
import Wrapper from '../assets/wrappers/DashboardFormPage';
import { Form, useSubmit, Link } from 'react-router-dom';
import { JOB_TYPE, JOB_STATUS, JOB_SORT_BY } from '../../../utils/constants';
import { useAllJobsContext } from '../pages/AllJobs';

const SearchContainer = () => {
  return (
    <Wrapper>
      <Form className='form'>
        <h5 className='form-title'>search form</h5>
        <div className='form-center'>
          {/* search position */}

          <FormRow type='search' name='search' defaultValue='a' />
          <FormRowSelect
            labelText='job status'
            name='jobStatus'
            list={['all', ...Object.values(JOB_STATUS)]}
            defaultValue='all'
          />
          <FormRowSelect
            labelText='job type'
            name='jobType'
            list={['all', ...Object.values(JOB_TYPE)]}
            defaultValue='all'
          />
          <FormRowSelect
            name='sort'
            defaultValue='newest'
            list={[...Object.values(JOB_SORT_BY)]}
          />

          <Link to='/dashboard/all-jobs' className='btn form-btn delete-btn'>
            Reset Search Values
          </Link>
          {/* TEMP!!!! */}
          <SubmitBtn formBtn />
        </div>
      </Form>
    </Wrapper>
  );
};

export default SearchContainer;
```

#### All Jobs Loader

AllJobs.jsx

```js
import { toast } from 'react-toastify';
import { JobsContainer, SearchContainer } from '../components';
import customFetch from '../utils/customFetch';
import { useLoaderData } from 'react-router-dom';
import { useContext, createContext } from 'react';
const AllJobsContext = createContext();
export const loader = async ({ request }) => {
  try {
    const params = Object.fromEntries([
      ...new URL(request.url).searchParams.entries(),
    ]);

    const { data } = await customFetch.get('/jobs', {
      params,
    });

    return {
      data,
      searchValues: { ...params },
    };
  } catch (error) {
    toast.error(error.response.data.msg);
    return error;
  }
};

const AllJobs = () => {
  const { data, searchValues } = useLoaderData();

  return (
    <AllJobsContext.Provider value={{ data, searchValues }}>
      <SearchContainer />
      <JobsContainer />
    </AllJobsContext.Provider>
  );
};
export default AllJobs;

export const useAllJobsContext = () => useContext(AllJobsContext);
```

```js
const params = Object.fromEntries([
  ...new URL(request.url).searchParams.entries(),
]);
```

new URL(request.url): This creates a new URL object by passing the request.url to the URL constructor. The URL object provides various methods and properties to work with URLs.

.searchParams: The searchParams property of the URL object gives you access to the query parameters in the URL. It is an instance of the URLSearchParams class, which provides methods to manipulate and access the parameters.

.entries(): The entries() method of searchParams returns an iterator containing arrays of key-value pairs for each query parameter. Each array contains two elements: the parameter name and its corresponding value.

([...new URL(request.url).searchParams.entries()]): The spread operator ... is used to convert the iterator obtained from searchParams.entries() into an array. This allows us to pass the array to the Object.fromEntries() method.

Object.fromEntries(): This static method creates an object from an array of key-value pairs. It takes an iterable (in this case, the array of parameter key-value pairs) and returns a new object where the keys and values are derived from the iterable.

Putting it all together, the code retrieves the URL from the request.url property, extracts the search parameters using the searchParams property, converts them into an array of key-value pairs using entries(), and finally uses Object.fromEntries() to create an object with the parameter names as keys and their corresponding values. The resulting object, params, contains all the search parameters from the URL.

#### Submit Form Programmatically

- setup default values from the context
- remove SubmitBtn
- add onChange to FormRow, FormRowSelect and all inputs

SearchContainer.js

```js
import { FormRow, FormRowSelect } from '.';
import Wrapper from '../assets/wrappers/DashboardFormPage';
import { Form, useSubmit, Link } from 'react-router-dom';
import { JOB_TYPE, JOB_STATUS, JOB_SORT_BY } from '../../../utils/constants';
import { useAllJobsContext } from '../pages/AllJobs';
const SearchContainer = () => {
  const { searchValues } = useAllJobsContext();
  const { search, jobStatus, jobType, sort } = searchValues;

  const submit = useSubmit();

  return (
    <Wrapper>
      <Form className='form'>
        <h5 className='form-title'>search form</h5>
        <div className='form-center'>
          {/* search position */}

          <FormRow
            type='search'
            name='search'
            defaultValue={search}
            onChange={(e) => {
              submit(e.currentTarget.form);
            }}
          />
          <FormRowSelect
            labelText='job status'
            name='jobStatus'
            list={['all', ...Object.values(JOB_STATUS)]}
            defaultValue={jobStatus}
            onChange={(e) => {
              submit(e.currentTarget.form);
            }}
          />
          <FormRowSelect
            labelText='job type'
            name='jobType'
            defaultValue={jobType}
            list={['all', ...Object.values(JOB_TYPE)]}
            onChange={(e) => {
              submit(e.currentTarget.form);
            }}
          />
          <FormRowSelect
            name='sort'
            defaultValue={sort}
            list={[...Object.values(JOB_SORT_BY)]}
            onChange={(e) => {
              submit(e.currentTarget.form);
            }}
          />
          <Link to='/dashboard/all-jobs' className='btn form-btn delete-btn'>
            Reset Search Values
          </Link>
        </div>
      </Form>
    </Wrapper>
  );
};

export default SearchContainer;
```

#### Debounce

[JS Nuggets - Debounce](https://youtu.be/tYx6pXdvt1s)

In JavaScript, debounce is a way to limit how often a function gets called. It helps prevent rapid or repeated function executions by introducing a delay. This is useful for tasks like handling user input, where you want to wait for a pause before triggering an action to avoid unnecessary processing.

```js
const debounce = (onChange) => {
  let timeout;
  return (e) => {
    const form = e.currentTarget.form;
    clearTimeout(timeout);
    timeout = setTimeout(() => {
      onChange(form);
    }, 2000);
  };
};
<FormRow
  type='search'
  name='search'
  defaultValue={search}
  onChange={debounce((form) => {
    submit(form);
  })}
/>;
```

#### Pagination - Setup

- create PageBtnContainer

JobsContainer.jsx

```js
import Job from './Job';
import Wrapper from '../assets/wrappers/JobsContainer';
import PageBtnContainer from './PageBtnContainer';
import { useAllJobsContext } from '../pages/AllJobs';

const JobsContainer = () => {
  const { data } = useAllJobsContext();
  const { jobs, totalJobs, numOfPages } = data;
  if (jobs.length === 0) {
    return (
      <Wrapper>
        <h2>No jobs to display...</h2>
      </Wrapper>
    );
  }

  return (
    <Wrapper>
      <h5>
        {totalJobs} job{jobs.length > 1 && 's'} found
      </h5>
      <div className='jobs'>
        {jobs.map((job) => {
          return <Job key={job._id} {...job} />;
        })}
      </div>
      {numOfPages > 1 && <PageBtnContainer />}
    </Wrapper>
  );
};

export default JobsContainer;
```

#### Basic PageBtnContainer

```js
import { HiChevronDoubleLeft, HiChevronDoubleRight } from 'react-icons/hi';
import Wrapper from '../assets/wrappers/PageBtnContainer';
import { useLocation, Link, useNavigate } from 'react-router-dom';
import { useAllJobsContext } from '../pages/AllJobs';

const PageBtnContainer = () => {
  const {
    data: { numOfPages, currentPage },
  } = useAllJobsContext();
  const { search, pathname } = useLocation();
  const navigate = useNavigate();
  const pages = Array.from({ length: numOfPages }, (_, index) => index + 1);

  const handlePageChange = (pageNumber) => {
    const searchParams = new URLSearchParams(search);
    searchParams.set('page', pageNumber);
    navigate(`${pathname}?${searchParams.toString()}`);
  };

  return (
    <Wrapper>
      <button
        className='btn prev-btn'
        onClick={() => {
          let prevPage = currentPage - 1;
          if (prevPage < 1) prevPage = numOfPages;
          handlePageChange(prevPage);
        }}
      >
        <HiChevronDoubleLeft />
        prev
      </button>
      <div className='btn-container'>
        {pages.map((pageNumber) => (
          <button
            className={`btn page-btn ${pageNumber === currentPage && 'active'}`}
            key={pageNumber}
            onClick={() => handlePageChange(pageNumber)}
          >
            {pageNumber}
          </button>
        ))}
      </div>
      <button
        className='btn next-btn'
        onClick={() => {
          let nextPage = currentPage + 1;
          if (nextPage > numOfPages) nextPage = 1;
          handlePageChange(nextPage);
        }}
      >
        next
        <HiChevronDoubleRight />
      </button>
    </Wrapper>
  );
};

export default PageBtnContainer;
```

#### Complex - PageBtnContainer

```js
import { HiChevronDoubleLeft, HiChevronDoubleRight } from 'react-icons/hi';
import Wrapper from '../assets/wrappers/PageBtnContainer';
import { useLocation, Link, useNavigate } from 'react-router-dom';
import { useAllJobsContext } from '../pages/AllJobs';

const PageBtnContainer = () => {
  const {
    data: { numOfPages, currentPage },
  } = useAllJobsContext();
  const { search, pathname } = useLocation();
  const navigate = useNavigate();

  const handlePageChange = (pageNumber) => {
    const searchParams = new URLSearchParams(search);
    searchParams.set('page', pageNumber);
    navigate(`${pathname}?${searchParams.toString()}`);
  };

  const addPageButton = ({ pageNumber, activeClass }) => {
    return (
      <button
        className={`btn page-btn ${activeClass && 'active'}`}
        key={pageNumber}
        onClick={() => handlePageChange(pageNumber)}
      >
        {pageNumber}
      </button>
    );
  };

  const renderPageButtons = () => {
    const pageButtons = [];

    // Add the first page button
    pageButtons.push(
      addPageButton({ pageNumber: 1, activeClass: currentPage === 1 })
    );
    // Add the dots before the current page if there are more than 3 pages
    if (currentPage > 3) {
      pageButtons.push(
        <span className='page-btn dots' key='dots-1'>
          ....
        </span>
      );
    }
    // one before current page
    if (currentPage !== 1 && currentPage !== 2) {
      pageButtons.push(
        addPageButton({ pageNumber: currentPage - 1, activeClass: false })
      );
    }

    // Add the current page button
    if (currentPage !== 1 && currentPage !== numOfPages) {
      pageButtons.push(
        addPageButton({ pageNumber: currentPage, activeClass: true })
      );
    }

    // one after current page
    if (currentPage !== numOfPages && currentPage !== numOfPages - 1) {
      pageButtons.push(
        addPageButton({ pageNumber: currentPage + 1, activeClass: false })
      );
    }
    if (currentPage < numOfPages - 2) {
      pageButtons.push(
        <span className=' page-btn dots' key='dots+1'>
          ....
        </span>
      );
    }

    // Add the last page button
    pageButtons.push(
      addPageButton({
        pageNumber: numOfPages,
        activeClass: currentPage === numOfPages,
      })
    );

    return pageButtons;
  };

  return (
    <Wrapper>
      <button
        className='prev-btn'
        onClick={() => {
          let prevPage = currentPage - 1;
          if (prevPage < 1) prevPage = numOfPages;
          handlePageChange(prevPage);
        }}
      >
        <HiChevronDoubleLeft />
        prev
      </button>
      <div className='btn-container'>{renderPageButtons()}</div>
      <button
        className='btn next-btn'
        onClick={() => {
          let nextPage = currentPage + 1;
          if (nextPage > numOfPages) nextPage = 1;
          handlePageChange(nextPage);
        }}
      >
        next
        <HiChevronDoubleRight />
      </button>
    </Wrapper>
  );
};

export default PageBtnContainer;
```

#### PageBtnContainer CSS (optional)

wrappers/PageBtnContainer.js

```js
import styled from 'styled-components';

const Wrapper = styled.section`
  height: 6rem;
  margin-top: 2rem;
  display: flex;
  align-items: center;
  justify-content: end;
  flex-wrap: wrap;
  gap: 1rem;
  .btn-container {
    background: var(--background-secondary-color);
    border-radius: var(--border-radius);
    display: flex;
  }
  .page-btn {
    background: transparent;
    border-color: transparent;
    width: 50px;
    height: 40px;
    font-weight: 700;
    font-size: 1.25rem;
    color: var(--primary-500);
    border-radius: var(--border-radius);
    cursor:pointer:
  }
  .active{
    background:var(--primary-500);
        color: var(--white);

  }
  .prev-btn,.next-btn{
    background: var(--background-secondary-color);
    border-color: transparent;
        border-radius: var(--border-radius);

    width: 100px;
    height: 40px;
        color: var(--primary-500);
text-transform:capitalize;
letter-spacing:var(--letter-spacing);
display:flex;
align-items:center;
justify-content:center;
gap:0.5rem;
cursor:pointer;
  }
  .prev-btn:hover,.next-btn:hover{
    background:var(--primary-500);
        color: var(--white);
        transition:var(--transition);
  }
.dots{
  display:grid;
  place-items:center;
  cursor:text;
}
`;
export default Wrapper;
```

#### Local Build

- remove default values from inputs in Register and Login
- navigate to client and build front-end

```sh
cd client && npm run build
```

- copy/paste all the files/folders

  - from client/dist
  - to server(root)/public

- in server.js point to index.html

```js
app.get('*', (req, res) => {
  res.sendFile(path.resolve(__dirname, './public', 'index.html'));
});
```

#### Deploy On Render

[Render](https://render.com/)

- sign up of for account
- create git repository

#### Build Front-End on Render

- add script
- change path

package.json

```js
 "scripts": {
    "setup-production-app": "npm i && cd client && npm i && npm run build",
  },
```

server.js

```js
app.use(express.static(path.resolve(__dirname, './client/dist')));

app.get('*', (req, res) => {
  res.sendFile(path.resolve(__dirname, './client/dist', 'index.html'));
});
```

#### Test Locally

- remove client/dist and client/node_modules
- remove node_modules and package-lock.json (optional)
- run "npm run setup-production-app", followed by "node server"

#### Test in Production

- change build command on render

```sh
npm run setup-production-app
```

- push up to github

#### Upload Image As Buffer

- remove public folder

```sh
npm i datauri@4.1.0
```

middleware/multerMiddleware.js

```js
import multer from 'multer';
import DataParser from 'datauri/parser.js';
import path from 'path';

const storage = multer.memoryStorage();
const upload = multer({ storage });

const parser = new DataParser();

export const formatImage = (file) => {
  const fileExtension = path.extname(file.originalname).toString();
  return parser.format(fileExtension, file.buffer).content;
};

export default upload;
```

controller/userController.js

```js
import { formatImage } from '../middleware/multerMiddleware.js';

export const updateUser = async (req, res) => {
  const newUser = { ...req.body };
  delete newUser.password;
  if (req.file) {
    const file = formatImage(req.file);
    const response = await cloudinary.v2.uploader.upload(file);
    newUser.avatar = response.secure_url;
    newUser.avatarPublicId = response.public_id;
  }
  const updatedUser = await User.findByIdAndUpdate(req.user.userId, newUser);

  if (req.file && updatedUser.avatarPublicId) {
    await cloudinary.v2.uploader.destroy(updatedUser.avatarPublicId);
  }
  res.status(StatusCodes.OK).json({ msg: 'update user' });
};
```

#### Setup Global Loading

- create loading component (import/export)
- check for loading in DashboardLayout page

components/Loading.jsx

```js
const Loading = () => {
  return <div className='loading'></div>;
};

export default Loading;
```

DashboardLayout.jsx

```js
import { useNavigation } from 'react-router-dom';
import { Loading } from '../components';

const DashboardLayout = ({ isDarkThemeEnabled }) => {
  const navigation = useNavigation();
  const isPageLoading = navigation.state === 'loading';

  return (
    <Wrapper>
      ...
      <div className='dashboard-page'>
        {isPageLoading ? <Loading /> : <Outlet context={{ user }} />}
      </div>
      ...
    </Wrapper>
  );
};
```

#### React Query

React Query is a powerful library that simplifies data fetching, caching, and synchronization in React applications. It provides a declarative and intuitive way to manage remote data by abstracting away the complex logic of fetching and caching data from APIs. React Query offers features like automatic background data refetching, optimistic updates, pagination support, and more, making it easier to build performant and responsive applications that rely on fetching and manipulating data.

[React Query Docs](https://tanstack.com/query/v4/docs/react/overview)

- in the client

```sh
npm i @tanstack/react-query@4.29.5 @tanstack/react-query-devtools@4.29.6
```

App.jsx

```js
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';
import { ReactQueryDevtools } from '@tanstack/react-query-devtools';

const queryClient = new QueryClient({
  defaultOptions: {
    queries: {
      staleTime: 1000 * 60 * 5,
    },
  },
});

const App = () => {
  return (
    <QueryClientProvider client={queryClient}>
      <RouterProvider router={router} />
      <ReactQueryDevtools initialIsOpen={false} />
    </QueryClientProvider>
  );
};
```

#### Page Error Element

- create components/ErrorElement

```js
import { useRouteError } from 'react-router-dom';

const Error = () => {
  const error = useRouteError();
  console.log(error);
  return <h4>There was an error...</h4>;
};
export default ErrorElement;
```

Stats.jsx

```js
export const loader = async () => {
  const response = await customFetch.get('/jobs/stats');
  return response.data;
};
```

App.jsx

```js
{
  path: 'stats',
  element: <Stats />,
  loader: statsLoader,
  errorElement: <h4>There was an error...</h4>
},
```

```js
{
  path: 'stats',
  element: <Stats />,
  loader: statsLoader,
  errorElement: <ErrorElement />,
},
```

#### First Query

- navigate to stats

Stats.jsx

```js
import { ChartsContainer, StatsContainer } from '../components';
import customFetch from '../utils/customFetch';
import { useLoaderData } from 'react-router-dom';
import { useQuery } from '@tanstack/react-query';

export const loader = async () => {
  return null;
};

const Stats = () => {
  const response = useQuery({
    queryKey: ['stats'],
    queryFn: () => customFetch.get('/jobs/stats'),
  });
  console.log(response);
  if (response.isLoading) {
    return <h1>Loading...</h1>;
  }
  return <h1>react query</h1>;
  return (
    <>
      <StatsContainer defaultStats={defaultStats} />
      {monthlyApplications?.length > 1 && (
        <ChartsContainer data={monthlyApplications} />
      )}
    </>
  );
};
export default Stats;
```

```js
const data = useQuery({
  queryKey: ['stats'],
  queryFn: () => customFetch.get('/jobs/stats'),
});
```

const data = useQuery({ ... });: This line declares a constant variable named data and assigns it the result of the useQuery hook. The useQuery hook is provided by React Query and is used to perform data fetching.

queryKey: ['stats'],: The queryKey property is an array that serves as a unique identifier for the query. In this case, the query key is set to ['stats'], indicating that this query is fetching statistics related to jobs.

queryFn: () => customFetch.get('/jobs/stats'),: The queryFn property specifies the function that will be executed when the query is triggered. In this case, it uses an arrow function that calls customFetch.get('/jobs/stats'). The customFetch object is likely a custom wrapper around the fetch function or an external HTTP client library, used to make the actual API request to retrieve job statistics.In React Query, the queryFn property expects a function that returns a promise. The promise should resolve with the data you want to fetch and store in the query cache.

customFetch.get('/jobs/stats'): This line is making an HTTP GET request to the /jobs/stats endpoint, which is the API route that provides the job statistics data.

#### Get Stats with React Query

```js
const statsQuery = {
  queryKey: ['stats'],
  queryFn: async () => {
    const response = await customFetch.get('/jobs/stats');
    return response.data;
  },
};

export const loader = async () => {
  return null;
};

const Stats = () => {
  const { isLoading, isError, data } = useQuery(statsQuery);

  if (isLoading) return <h4>Loading...</h4>;
  if (isError) return <h4>Error...</h4>;
  // after loading/error or ?.
  const { defaultStats, monthlyApplications } = data;

  return (
    <>
      <StatsContainer defaultStats={defaultStats} />
      {monthlyApplications?.length > 1 && (
        <ChartsContainer data={monthlyApplications} />
      )}
    </>
  );
};
export default Stats;
```

#### React Query in Stats Loader

App.jsx

```js
{
  path: 'stats',
  element: <Stats />,
  loader: statsLoader(queryClient),
  errorElement: <ErrorElement />,
},
```

Stats.jsx

```js
import { ChartsContainer, StatsContainer } from '../components';
import customFetch from '../utils/customFetch';
import { useQuery } from '@tanstack/react-query';

const statsQuery = {
  queryKey: ['stats'],
  queryFn: async () => {
    const response = await customFetch.get('/jobs/statss');
    return response.data;
  },
};

export const loader = (queryClient) => async () => {
  const data = await queryClient.ensureQueryData(statsQuery);
  return data;
};

const Stats = () => {
  const { data } = useQuery(statsQuery);
  const { defaultStats, monthlyApplications } = data;

  return (
    <>
      <StatsContainer defaultStats={defaultStats} />
      {monthlyApplications?.length > 1 && (
        <ChartsContainer data={monthlyApplications} />
      )}
    </>
  );
};
export default Stats;
```

#### React Query for Current User

DashboardLayout.jsx

```js
const userQuery = {
  queryKey: ['user'],
  queryFn: async () => {
    const { data } = await customFetch('/users/current-user');
    return data;
  },
};

export const loader = (queryClient) => async () => {
  try {
    return await queryClient.ensureQueryData(userQuery);
  } catch (error) {
    return redirect('/');
  }
};

const Dashboard = ({ prefersDarkMode, queryClient }) => {
  const { user } = useQuery(userQuery)?.data;
};
```

#### Invalidate Queries

Login.jsx

```js
export const action =
  (queryClient) =>
  async ({ request }) => {
    const formData = await request.formData();
    const data = Object.fromEntries(formData);
    try {
      await axios.post('/api/v1/auth/login', data);
      queryClient.invalidateQueries();
      toast.success('Login successful');
      return redirect('/dashboard');
    } catch (error) {
      toast.error(error.response.data.msg);
      return error;
    }
  };
```

DashboardLayout.jsx

```js
const logoutUser = async () => {
  navigate('/');
  await customFetch.get('/auth/logout');
  queryClient.invalidateQueries();
  toast.success('Logging out...');
};
```

Profile.jsx

```js
export const action =
  (queryClient) =>
  async ({ request }) => {
    const formData = await request.formData();
    const file = formData.get('avatar');
    if (file && file.size > 500000) {
      toast.error('Image size too large');
      return null;
    }
    try {
      await customFetch.patch('/users/update-user', formData);
      queryClient.invalidateQueries(['user']);
      toast.success('Profile updated successfully');
      return redirect('/dashboard');
    } catch (error) {
      toast.error(error?.response?.data?.msg);
      return null;
    }
  };
```

#### All Jobs Query

AllJobs.jsx

```js
import { toast } from 'react-toastify';
import { JobsContainer, SearchContainer } from '../components';
import customFetch from '../utils/customFetch';
import { useLoaderData } from 'react-router-dom';
import { useContext, createContext } from 'react';
import { useQuery } from '@tanstack/react-query';
const AllJobsContext = createContext();

const allJobsQuery = (params) => {
  const { search, jobStatus, jobType, sort, page } = params;
  return {
    queryKey: [
      'jobs',
      search ?? '',
      jobStatus ?? 'all',
      jobType ?? 'all',
      sort ?? 'newest',
      page ?? 1,
    ],
    queryFn: async () => {
      const { data } = await customFetch.get('/jobs', {
        params,
      });
      return data;
    },
  };
};

export const loader =
  (queryClient) =>
  async ({ request }) => {
    const params = Object.fromEntries([
      ...new URL(request.url).searchParams.entries(),
    ]);

    await queryClient.ensureQueryData(allJobsQuery(params));
    return { searchValues: { ...params } };
  };

const AllJobs = () => {
  const { searchValues } = useLoaderData();
  const { data } = useQuery(allJobsQuery(searchValues));
  return (
    <AllJobsContext.Provider value={{ data, searchValues }}>
      <SearchContainer />
      <JobsContainer />
    </AllJobsContext.Provider>
  );
};
export default AllJobs;

export const useAllJobsContext = () => useContext(AllJobsContext);
```

#### Invalidate Jobs

AddJob.jsx

```js
export const action =
  (queryClient) =>
  async ({ request }) => {
    const formData = await request.formData();
    const data = Object.fromEntries(formData);
    try {
      await customFetch.post('/jobs', data);
      queryClient.invalidateQueries(['jobs']);
      toast.success('Job added successfully ');
      return redirect('all-jobs');
    } catch (error) {
      toast.error(error?.response?.data?.msg);
      return error;
    }
  };
```

EditJob.jsx

```js
export const action =
  (queryClient) =>
  async ({ request, params }) => {
    const formData = await request.formData();
    const data = Object.fromEntries(formData);
    try {
      await customFetch.patch(`/jobs/${params.id}`, data);
      queryClient.invalidateQueries(['jobs']);
      toast.success('Job edited successfully');
      return redirect('/dashboard/all-jobs');
    } catch (error) {
      toast.error(error?.response?.data?.msg);
      return error;
    }
  };
```

DeleteJob.jsx

```js
export const action =
  (queryClient) =>
  async ({ params }) => {
    try {
      await customFetch.delete(`/jobs/${params.id}`);
      queryClient.invalidateQueries(['jobs']);
      toast.success('Job deleted successfully');
    } catch (error) {
      toast.error(error?.response?.data?.msg);
    }
    return redirect('/dashboard/all-jobs');
  };
```

#### Edit Job Loader

```js
import { FormRow, FormRowSelect, SubmitBtn } from '../components';
import Wrapper from '../assets/wrappers/DashboardFormPage';
import { useLoaderData, useParams } from 'react-router-dom';
import { JOB_STATUS, JOB_TYPE } from '../../../utils/constants';
import { Form, redirect } from 'react-router-dom';
import { toast } from 'react-toastify';
import customFetch from '../utils/customFetch';
import { useQuery } from '@tanstack/react-query';

const singleJobQuery = (id) => {
  return {
    queryKey: ['job', id],
    queryFn: async () => {
      const { data } = await customFetch.get(`/jobs/${id}`);
      return data;
    },
  };
};

export const loader =
  (queryClient) =>
  async ({ params }) => {
    try {
      await queryClient.ensureQueryData(singleJobQuery(params.id));
      return params.id;
    } catch (error) {
      toast.error(error?.response?.data?.msg);
      return redirect('/dashboard/all-jobs');
    }
  };

export const action =
  (queryClient) =>
  async ({ request, params }) => {
    const formData = await request.formData();
    const data = Object.fromEntries(formData);
    try {
      await customFetch.patch(`/jobs/${params.id}`, data);
      queryClient.invalidateQueries(['jobs']);

      toast.success('Job edited successfully');
      return redirect('/dashboard/all-jobs');
    } catch (error) {
      toast.error(error?.response?.data?.msg);
      return error;
    }
  };

const EditJob = () => {
  const id = useLoaderData();

  const {
    data: { job },
  } = useQuery(singleJobQuery(id));

  return (
    <Wrapper>
      <Form method='post' className='form'>
        <h4 className='form-title'>edit job</h4>
        <div className='form-center'>
          <FormRow type='text' name='position' defaultValue={job.position} />
          <FormRow type='text' name='company' defaultValue={job.company} />
          <FormRow
            type='text'
            name='jobLocation'
            labelText='job location'
            defaultValue={job.jobLocation}
          />
          <FormRowSelect
            name='jobStatus'
            labelText='job status'
            defaultValue={job.jobStatus}
            list={Object.values(JOB_STATUS)}
          />
          <FormRowSelect
            name='jobType'
            labelText='job type'
            defaultValue={job.jobType}
            list={Object.values(JOB_TYPE)}
          />
          <SubmitBtn formBtn />
        </div>
      </Form>
    </Wrapper>
  );
};
export default EditJob;
```

#### Axios Interceptors

DashboardLayout.jsx

```js
const DashboardContext = createContext();

const DashboardLayout = ({ isDarkThemeEnabled }) => {
  const [isAuthError, setIsAuthError] = useState(false);

  const logoutUser = async () => {
    await customFetch.get('/auth/logout');
    toast.success('Logging out...');
    navigate('/');
  };

  customFetch.interceptors.response.use(
    (response) => {
      return response;
    },
    (error) => {
      if (error?.response?.status === 401) {
        setIsAuthError(true);
      }
      return Promise.reject(error);
    }
  );
  useEffect(() => {
    if (!isAuthError) return;
    logoutUser();
  }, [isAuthError]);
  return (
    ...
  )
};

```

#### Security

```sh
npm install helmet express-mongo-sanitize express-rate-limit

```

Package: helmet
Description: helmet is a security package for Express.js applications that helps protect them by setting various HTTP headers to enhance security, prevent common web vulnerabilities, and improve overall application security posture.
Need: The package is needed to safeguard web applications from potential security threats, such as cross-site scripting (XSS) attacks, clickjacking, and other security exploits.

Package: express-mongo-sanitize
Description: express-mongo-sanitize is a middleware for Express.js that sanitizes user-supplied data coming from request parameters, body, and query strings to prevent potential NoSQL injection attacks on MongoDB databases.
Need: The package addresses the need to protect MongoDB databases from malicious attempts to manipulate data and helps ensure the integrity of data storage and retrieval.

Package: express-rate-limit
Description: express-rate-limit is an Express.js middleware that helps control and limit the rate of incoming requests from a specific IP address or a set of IP addresses to protect the server from abuse, brute-force attacks, and potential denial-of-service (DoS) attacks.
Need: This package is necessary to manage and regulate the number of requests made to the server within a given time frame, preventing excessive usage and improving the overall stability and performance of the application.

server.js

```js
import helmet from 'helmet';
import mongoSanitize from 'express-mongo-sanitize';

app.use(helmet());
app.use(mongoSanitize());
```

routes/authRouter.js

```js
import rateLimiter from 'express-rate-limit';

const apiLimiter = rateLimiter({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 15,
  message: { msg: 'IP rate limit exceeded, retry in 15 minutes.' },
});
router.post('/register', apiLimiter, validateRegisterInput, register);
router.post('/login', apiLimiter, validateLoginInput, login);
```

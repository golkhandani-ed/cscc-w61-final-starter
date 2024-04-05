# Assignment: Cloning and Replicating a Website

## Objective
Your task is to clone and replicate the functionality of the provided website: [https://cscc-w61-final.vercel.app/](https://cscc-w61-final.vercel.app/). This website displays a contact list using GitHub usernames, along with detailed user information.

## Requirements

### Website Structure

#### Main Page
- The main page serves as a landing page.
- It should include links or buttons to navigate to other sections of the website.

#### Users Page
- The users page should include a sidebar and a content section.
- Sidebar:
  - Include a search box allowing users to search for GitHub usernames.
  - Display a list of users below the search box.
  - Implement dynamic fetching of data from the GitHub API to show suggested users as the user types in the search box.
- Content Section:
  - Clicking on any username in the sidebar should display a card with detailed GitHub user information.
  - Highlight the selected user in the sidebar.

### Implementation Guidelines

#### GitHub API Usage
- Utilize the GitHub API to fetch user data based on usernames.
- Implement search functionality using GitHub search API.
- Retrieve information such as username, real name, email, phone, profile picture, and any other available data for each GitHub user.

#### Frontend Development
- Use Next JS without any use of State Management package like Redux, etc.
- Try to think about the routing and structure of the website before start coding
- Be creative about the user interface but you can use the CSS below if you want to focus on Next.js only

#### Code Organization
- Organize your code into separate files or components for better maintainability.
- Follow best practices for code readability and maintainability.

#### Testing
- Test the functionality of the website thoroughly to ensure all features work as expected.
- Perform cross-browser and cross-device testing to ensure compatibility.

### Submission Guidelines

#### GitHub Repository
- Create a GitHub repository to host your project.
- Include a README file with instructions on how to run the project locally.
- Ensure the repository is well-documented, including information about dependencies and any setup instructions.

#### Deployment
- Optionally, deploy the website to a hosting platform such as Vercel, Netlify, or GitHub Pages for demonstration purposes.
- Provide a link to the deployed website in your README file.

### Submission
- Submit the GitHub repository link along with any additional instructions or notes through the designated submission channel.

## Note
Ensure that your implementation adheres to legal and ethical considerations, including compliance with the terms of use of the GitHub API and any applicable data protection regulations. Respect user privacy and do not store or misuse personal information obtained through the API.


## Final Result Images

##### Landing PAGE

![Landing page](https://cscc-w61-final.vercel.app/landing_page.png)
##### Users with selected item PAGE

![Get user info](https://cscc-w61-final.vercel.app/users_selected.png)
##### Users with query PAGE

![Get users by query](https://cscc-w61-final.vercel.app/users_query.png)

##### GLOBAL CSS


```css
:root {
  /* Primary Colors */
  --primary-color: rgba(255, 187, 0, 1);
  --on-primary-color: rgba(0, 0, 0, 1);
  --primary-container-color: rgb(244, 219, 178);
  --on-primary-container-color: rgba(0, 0, 0, 1);

  /* Secondary Colors */
  --secondary-color: rgba(5, 106, 152, 1);
  --on-secondary-color: rgba(255, 255, 255, 1);




  /* Background Colors */
  --background-color: rgba(249, 246, 241, 1);
  --on-background-color: rgba(0, 0, 0, 1);



  /* Text Field Colors */
  --text-field-background-color: rgb(240, 119, 6);
  --on-text-field-background-color: rgba(0, 0, 0, 1);
  --border-radius: 8px;
  --gap: 12px;
  --regular-height: 48px;
  --btn-height: 48px;
  --focus-border: 2px var(--primary-color) solid;
  --active-border: 2px transparent solid;

}

* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

html,
body {
  min-height: 100vh;
  width: 100%;
  background-color: var(--background-color);
}

/* SHARED ELEMENTS */
.link-button {
  padding: 0 32px;
  background-color: var(--primary-color);
  color: var(--on-primary-color);
  border: 0;
  outline: 0;
  border-radius: var(--border-radius);
  cursor: pointer;
  text-transform: uppercase;
  font-weight: 500;
  text-align: center;
  text-decoration: none;
  height: var(--btn-height);
  line-height: var(--btn-height);
}


/* LANDING PAGE */
.landing {
  height: 100vh;
  width: 100%;
  background-color: var(--background-color);
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: center;
  text-align: center;
  align-items: center;
}

.landing__logo {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  gap: 4rem;
}

.landing__title {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
  justify-content: center;
  max-height: 20vh;
  margin: 1rem;
}

.landing__actions {
  display: flex;
  flex-direction: row;
  gap: calc(4 * var(--gap));
  justify-content: center;
  align-items: center;
}




/* FEATURES LAYOUT */

.users-page__container {
  position: relative;
  background-color: var(--background-color);
  height: 100vh;
  display: flex;
}

.users-page__menu {
  position: fixed;
  background-color: var(--primary-container-color);
  width: 100%;
  max-width: 33%;
  height: 100%;
  z-index: 10;
  text-align: center;
  filter: drop-shadow(2px 2px 4px rgba(72, 72, 72, 0.3));
}

.users-page__content {
  position: absolute;
  right: 0;
  width: 67%;
}


/* SEARCH BAR */

input[type="search"]::-webkit-search-cancel-button {
  -webkit-appearance: none;
  height: 1em;
  width: 1em;
  border-radius: 50em;
  background: url(https://pro.fontawesome.com/releases/v5.10.0/svgs/solid/times-circle.svg) no-repeat 50% 50%;
  background-size: contain;
  opacity: 0;
  pointer-events: none;
}

input[type="search"]:focus::-webkit-search-cancel-button {
  opacity: 1;
  pointer-events: all;
  filter: invert(1);
}

.search_bar__container {
  width: calc(100% - 32px);
  height: 80px;
  margin-top: 32px;
  margin-inline: 16px;
  background-color: transparent;
  text-align: start;
}

.search_bar__label {
  font-size: .8rem;
  font-weight: bold;
}

.search_bar__input {
  outline: none;
  width: 100%;
  height: var(--btn-height);
  padding: 0.5em;
  margin-top: 8px;
  border: 0;
  border-radius: var(--border-radius);
  background-color: var(--text-field-background-color);
  color: var(--on-text-field-background-color);
  font-size: 1rem;
}

.search_bar__input:focus,
.search_bar__input:hover {
  outline: var(--focus-border);
  border: 0;
}

.search_bar__input::placeholder {
  font-weight: 500;
  opacity: 0.5;
  color: var(--on-text-field-background-color);
}

/* USER LIST */

.user-list__container {
  height: calc(100vh - 80px - 48px);
  overflow: scroll;
}

.user-list__row {
  position: relative;
  list-style: none;
  background-color: transparent;
  margin: .5rem 0;
  padding: 0.5rem;
  border-radius: var(--border-radius);
  height: var(--btn-height);
  line-height: var(--btn-height);
}

.user-list__row a {
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 100%;
  border-radius: var(--border-radius);
  color: var(--on-background-color);
  background-color: var(--background-color);
  text-decoration: none;
}

.user-list__selected-user a {
  background-color: var(--primary-color);
  color: var(--on-primary-color);
  text-decoration: none;
}



/* USER DETAILS */
.user-details__container {
  height: 100%;
  padding: 1rem;
}

.user-details__header {
  text-transform: capitalize;
}

/* USER CARD */

.user-card__container {
  max-width: 480px;
  margin: 0 auto;
  background-color: wheat;
  padding: 32px;
  border-radius: var(--border-radius);
  border: var(--focus-border);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

hr {
  color: red;
}

.avatar-img {
  border-radius: 50%;
  width: 100%;
  height: 100%;
  max-width: 400px;
  max-height: 400px;
  filter: drop-shadow(2px 2px 4px rgba(41, 41, 41, 0.679));
  margin: 32px auto;
}

.user-card__row {
  width: 100%;
  height: var(--btn-height);
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

```


##### API CALLS

```ts
export type UserSummary = {
  login: string;
  id: number;
  avatar_url: string;
  url: string;
};

export type User = {
  login: string;
  id: number;
  avatar_url: string;
  html_url: string;
  name: string;
  blog: string;
  email: null;
  bio: string;
  public_repos: number;
  public_gists: number;
  followers: number;
  following: number;
  created_at: Date;
  updated_at: Date;
};

export async function getInitUsers(): Promise<UserSummary[]> {
  try {
    const res = await fetch(`https://api.github.com/users`);
    const items = await res.json();
    return items;
  } catch (error) {
    return [];
  }
}

export async function getUsersByQuery(query: string): Promise<UserSummary[]> {
  try {
    const res = await fetch(`https://api.github.com/search/users?q=${query}`);
    const { items } = await res.json();
    return items;
  } catch (error) {
    return [];
  }
}

export async function getUserByLogin(login: string): Promise<User | undefined> {
  try {
    const res = await fetch("https://api.github.com/users/" + login);
    const user = await res.json();
    return user;
  } catch (error) {
    return;
  }
}

```
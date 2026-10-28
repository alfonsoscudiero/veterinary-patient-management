# Veterinary Patient Management App

A veterinary patient management application developed with Vue 3, JavaScript, Vite, and Tailwind CSS.

This project was built while following the **Vue.js course by Código con Juan**. Its purpose is to practice Vue 3 fundamentals, component communication, reactive state management, form validation, and browser data persistence.

## Live Demo

Try the application here: [Veterinary Patient Management – Vue 3](https://veterinary-patients-vue.netlify.app/)

The application is deployed on Netlify and connected to GitHub for automatic deployment when changes are pushed to the `main` branch.

## Features

- Register new veterinary patients.
- Edit existing patient information.
- Delete patients from the list.
- Validate required form fields.
- Display success and error alerts.
- Generate unique patient IDs using `uid`.
- Save patient information in localStorage.
- Automatically restore saved patients after refreshing the browser.

## Technologies Used

- Vue 3 (Composition API)
- JavaScript
- Vite
- Tailwind CSS
- HTML5 and CSS3
- uid

## Vue Concepts Practiced

**Reactive State:** Used `ref()` and `reactive()` to manage patient information.

**Component Communication:** Used `defineProps()`, `defineEmits()`, and component `v-model` to share and update data between parent and child components.

**Computed Properties:** Used `computed()` to dynamically change the submit button text when registering or editing patients.

**Data Persistence:** Used `watch()` with `{ deep: true }` to detect changes and automatically save patients to localStorage. Used `onMounted()` and `JSON.parse()` to restore saved information when the application loads.

**JavaScript Methods:** Practiced `push()`, `findIndex()`, `filter()`, `Object.assign()`, and the spread operator (`...`).

### Data Persistence

The application uses the browser's `localStorage` to save patient records without requiring a backend or database.

- `watch()` monitors changes to the patients array.
- `JSON.stringify()` converts patient data into a JSON string before saving it.
- `localStorage.setItem()` stores the data in the browser.
- `onMounted()` retrieves saved records when the application loads.
- `JSON.parse()` converts the stored JSON string back into JavaScript objects.

**Important:** Patient records are stored locally in each visitor's browser, not in a shared database. Each visitor has their own independent records. Data is not synchronized between users, browsers, or devices.

## Project Structure

```text
admin-pacientes/
├── public/
├── src/
│   ├── components/
│   │   ├── Alerta.vue
│   │   ├── Formulario.vue
│   │   ├── Header.vue
│   │   └── Paciente.vue
│   ├── App.vue
│   ├── main.js
│   └── style.css
├── index.html
├── package.json
├── README.md
└── vite.config.js
```

## Installation

Clone the repository:

```bash
git clone <repository-url>
```

Navigate to the application directory:

```bash
cd admin-pacientes
```

Install the dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Open the local URL displayed by Vite.

## What I Learned

Through this project, I practiced managing reactive data in Vue 3, sharing state between components, and implementing CRUD operations (Create, Read, Update, Delete).

I also learned how to use localStorage to preserve information between browser sessions and how to organize a Vue application into reusable components.

## Future Improvements

- Add a confirmation dialog before deleting patients.
- Improve form validation.
- Implement patient search and filtering.
- Connect the application to a backend API and database.

## Credits

Developed as a learning project following the Vue.js course by **Código con Juan**.

## Project Status

Deployed and functional.

The application supports patient registration, editing, deletion, form validation, and data persistence using localStorage.

Built with Vue 3, Vite, and Tailwind CSS as a learning project following the Vue.js course by Código con Juan.

Note: This application is intended for educational and portfolio purposes. Patient information is stored locally in the browser and should not be used to manage real veterinary medical records.

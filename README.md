# Veterinary Patient Management App

A veterinary patient management application developed with Vue 3, JavaScript, Vite, and Tailwind CSS.

This project was built while following the **Vue.js course by Código con Juan**. Its purpose is to practice Vue 3 fundamentals, component communication, reactive state management, form validation, and browser data persistence.

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

Learning project with functional patient registration, editing, deletion, and localStorage persistence.

Patient information is stored locally in the browser. This application is intended for educational purposes, not for managing real veterinary medical records.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Management System</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        :root {
            --font-size: 14px;
            --purple-600: #9333ea;
            --purple-700: #7c3aed;
            --purple-50: #faf5ff;
            --green-500: #10b981;
            --green-600: #059669;
            --green-50: #ecfdf5;
            --blue-500: #3b82f6;
            --blue-600: #2563eb;
            --blue-50: #eff6ff;
            --gray-50: #f9fafb;
            --gray-100: #f3f4f6;
            --red-500: #ef4444;
            --red-50: #fef2f2;
        }

        html {
            font-size: var(--font-size);
        }

        body {
            font-family: system-ui, -apple-system, sans-serif;
            margin: 0;
            padding: 0;
        }

        .hidden {
            display: none !important;
        }

        .card {
            background: white;
            border-radius: 0.5rem;
            box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1);
            padding: 1.5rem;
            position: relative;
        }

        .button {
            background-color: var(--purple-600);
            color: white;
            border: none;
            border-radius: 0.375rem;
            padding: 0.5rem 1rem;
            cursor: pointer;
            font-weight: 500;
            transition: background-color 0.2s;
        }

        .button:hover {
            background-color: var(--purple-700);
        }

        .button-green {
            background-color: var(--green-500);
        }

        .button-green:hover {
            background-color: var(--green-600);
        }

        .button-blue {
            background-color: var(--blue-500);
        }

        .button-blue:hover {
            background-color: var(--blue-600);
        }

        .button-outline {
            background-color: transparent;
            color: var(--purple-600);
            border: 1px solid var(--purple-600);
        }

        .button-outline:hover {
            background-color: var(--purple-50);
        }

        .button-ghost {
            background-color: transparent;
            color: var(--purple-600);
            border: none;
        }

        .button-ghost:hover {
            background-color: var(--purple-50);
        }

        .input {
            width: 100%;
            padding: 0.5rem;
            border: 1px solid #d1d5db;
            border-radius: 0.375rem;
            font-size: 0.875rem;
        }

        .input:focus {
            outline: none;
            border-color: var(--purple-600);
            box-shadow: 0 0 0 1px var(--purple-600);
        }

        .label {
            display: block;
            font-weight: 500;
            margin-bottom: 0.25rem;
            color: #374151;
        }

        .checkbox-container {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .checkbox {
            width: 1rem;
            height: 1rem;
            cursor: pointer;
        }

        .icon-button {
            position: absolute;
            top: 0.5rem;
            right: 0.5rem;
            background: none;
            border: none;
            cursor: pointer;
            padding: 0.5rem;
            border-radius: 0.25rem;
        }

        .icon-button:hover {
            background-color: var(--purple-50);
        }

        .student-card {
            background-color: var(--green-500);
            color: white;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        .student-card:hover {
            background-color: var(--green-600);
        }

        .selected-internship {
            background-color: var(--green-50);
            border-left: 4px solid var(--green-500);
            padding: 0.5rem;
            border-radius: 0.25rem;
            font-size: 0.875rem;
        }

        .available-internship {
            background-color: var(--gray-50);
            padding: 0.5rem;
            border-radius: 0.25rem;
            font-size: 0.875rem;
        }

        .internship-item {
            background-color: var(--blue-50);
            padding: 0.5rem;
            border-radius: 0.25rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .remove-button {
            background: none;
            border: none;
            color: var(--red-500);
            cursor: pointer;
            padding: 0.25rem;
        }

        .remove-button:hover {
            background-color: var(--red-50);
            border-radius: 0.25rem;
        }
    </style>
</head>
<body class="min-h-screen bg-purple-600 p-8">
    <div class="max-w-4xl mx-auto">
        <!-- Initial View -->
        <div id="initial-view" class="flex flex-col items-center justify-center min-h-[80vh] space-y-6">
            <h1 class="text-white text-3xl mb-8">Student Management System</h1>
            <div class="space-y-4">
                <button onclick="showView('admin-login')" class="button w-64 h-12 bg-white text-purple-600 hover:bg-gray-100">
                    Log in as Administrator
                </button>
                <button onclick="showView('student-auth')" class="button w-64 h-12 bg-white text-purple-600 hover:bg-gray-100">
                    Log in as Student
                </button>
            </div>
        </div>

        <!-- Student Auth View -->
        <div id="student-auth-view" class="hidden flex flex-col items-center justify-center min-h-[80vh]">
            <div class="card w-96">
                <button onclick="showView('initial')" class="icon-button">✕</button>
                <h2 class="text-center text-purple-600 text-xl font-medium mb-6">Student Access</h2>
                <div class="space-y-4">
                    <div>
                        <label class="label" for="username">Username</label>
                        <input class="input" id="username" type="text" placeholder="Enter username">
                    </div>
                    <div>
                        <label class="label" for="password">Password (min 8 characters)</label>
                        <input class="input" id="password" type="password" placeholder="Enter password">
                    </div>
                    <div class="space-y-2">
                        <button id="register-button" onclick="handleStudentRegister()" class="button w-full">
                            Register
                        </button>
                        <button id="login-button" onclick="handleStudentLogin()" class="button w-full hidden">
                            Log In
                        </button>
                        <button onclick="toggleAuthMode()" class="button-ghost w-full">
                            <span id="auth-toggle-text">Already have an account? Log In</span>
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Student Card View -->
        <div id="student-card-view" class="hidden flex flex-col items-center justify-center min-h-[80vh]">
            <div class="card w-96">
                <button onclick="showView('student-auth')" class="icon-button">✕</button>
                <h2 class="text-center text-purple-600 text-xl font-medium mb-6">Student Card</h2>
                <div class="space-y-4">
                    <div>
                        <label class="label" for="firstName">First Name</label>
                        <input class="input" id="firstName" type="text" placeholder="Enter first name">
                    </div>
                    <div>
                        <label class="label" for="lastName">Last Name</label>
                        <input class="input" id="lastName" type="text" placeholder="Enter last name">
                    </div>
                    <div>
                        <label class="label" for="studentClass">Class</label>
                        <input class="input" id="studentClass" type="text" placeholder="Enter class">
                    </div>

                    <div id="internships-section" class="space-y-2 hidden">
                        <div class="flex items-center justify-between">
                            <span class="label">Available Internships</span>
                            <button onclick="toggleInternshipsDisplay()" class="button-ghost">
                                <span id="chevron-icon">▼</span>
                            </button>
                        </div>

                        <div id="internships-display" class="space-y-2 hidden">
                            <div id="available-internships" class="space-y-2 max-h-32 overflow-y-auto"></div>
                            <button onclick="showView('student-select-internships')" class="button-blue w-full">
                                Select Internships
                            </button>
                        </div>

                        <div id="selected-internships-display" class="space-y-2 hidden">
                            <span class="label">My Selected Internships</span>
                            <div id="selected-internships-list" class="space-y-1"></div>
                        </div>
                    </div>

                    <button onclick="handleStudentCardSubmit()" class="button w-full">
                        Send
                    </button>
                </div>
            </div>
        </div>

        <!-- Student Select Internships View -->
        <div id="student-select-internships-view" class="hidden flex flex-col items-center justify-center min-h-[80vh]">
            <div class="card w-96">
                <button onclick="showView('student-card')" class="icon-button">✕</button>
                <h2 class="text-center text-purple-600 text-xl font-medium mb-6">Select Internships</h2>
                <div class="space-y-4">
                    <div>
                        <span class="label">Choose your internships:</span>
                        <div id="internship-checkboxes" class="space-y-3 mt-2 max-h-64 overflow-y-auto"></div>
                    </div>

                    <div class="space-y-2">
                        <button onclick="saveInternshipSelections()" class="button w-full">
                            <span id="save-button-text">Save Selections (0)</span>
                        </button>
                        <button onclick="showView('student-card')" class="button-outline w-full">
                            Cancel
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Admin Login View -->
        <div id="admin-login-view" class="hidden flex flex-col items-center justify-center min-h-[80vh]">
            <div class="card w-96">
                <button onclick="showView('initial')" class="icon-button">✕</button>
                <h2 class="text-center text-purple-600 text-xl font-medium mb-6">Administrator Login</h2>
                <div class="space-y-4">
                    <div>
                        <label class="label" for="adminPassword">Administrator Password</label>
                        <input class="input" id="adminPassword" type="password" placeholder="Enter administrator password">
                    </div>
                    <button onclick="handleAdminLogin()" class="button w-full">
                        Log In
                    </button>
                </div>
            </div>
        </div>

        <!-- Admin Dashboard View -->
        <div id="admin-dashboard-view" class="hidden space-y-8">
            <div class="flex items-center justify-between">
                <h1 class="text-white text-3xl">Administrator Dashboard</h1>
                <button onclick="showView('initial')" class="button-ghost text-white">✕</button>
            </div>

            <div class="flex flex-col items-center space-y-6">
                <button onclick="showView('admin-classes')" class="button-green w-64 h-12">
                    View Students
                </button>
                <button onclick="showView('admin-add-internships')" class="button-blue w-64 h-12">
                    Add Internships
                </button>
            </div>
        </div>

        <!-- Admin Classes View -->
        <div id="admin-classes-view" class="hidden space-y-8">
            <div class="flex items-center justify-between">
                <h1 class="text-white text-3xl">Classes</h1>
                <button onclick="showView('admin-dashboard')" class="button-ghost text-white">✕</button>
            </div>

            <div id="classes-list" class="grid gap-4"></div>
        </div>

        <!-- Admin Students by Class View -->
        <div id="admin-students-by-class-view" class="hidden space-y-8">
            <div class="flex items-center justify-between">
                <h1 class="text-white text-3xl">Class <span id="selected-class-name"></span> - Students</h1>
                <button onclick="showView('admin-classes')" class="button-ghost text-white">✕</button>
            </div>

            <div id="students-by-class-list" class="grid gap-4"></div>
        </div>

        <!-- Admin View Student Card -->
        <div id="admin-view-student-card-view" class="hidden flex flex-col items-center justify-center min-h-[80vh]">
            <div class="card w-96">
                <button onclick="showView('admin-students-by-class')" class="icon-button">✕</button>
                <h2 class="text-center text-purple-600 text-xl font-medium mb-6">Student Card</h2>
                <div class="space-y-4">
                    <div>
                        <span class="label">First Name</span>
                        <div id="view-firstName" class="p-2 bg-gray-50 rounded"></div>
                    </div>
                    <div>
                        <span class="label">Last Name</span>
                        <div id="view-lastName" class="p-2 bg-gray-50 rounded"></div>
                    </div>
                    <div>
                        <span class="label">Class</span>
                        <div id="view-class" class="p-2 bg-gray-50 rounded"></div>
                    </div>

                    <div id="view-available-internships" class="space-y-2 hidden">
                        <span class="label">Available Internships</span>
                        <div id="view-available-internships-list" class="space-y-2"></div>
                    </div>

                    <div id="view-selected-internships" class="space-y-2 hidden">
                        <span class="label">Student's Selected Internships</span>
                        <div id="view-selected-internships-list" class="space-y-1"></div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Admin Add Internships View -->
        <div id="admin-add-internships-view" class="hidden space-y-8">
            <div class="flex items-center justify-between">
                <h1 class="text-white text-3xl">Manage Internship Template</h1>
                <button onclick="showView('admin-dashboard')" class="button-ghost text-white">✕</button>
            </div>

            <div class="flex flex-col items-center">
                <div class="card w-96">
                    <h2 class="text-center text-purple-600 text-xl font-medium mb-6">Student Card Template</h2>
                    <div class="space-y-4">
                        <div>
                            <span class="label">First Name</span>
                            <div class="p-2 bg-gray-100 rounded text-gray-500">[Student First Name]</div>
                        </div>
                        <div>
                            <span class="label">Last Name</span>
                            <div class="p-2 bg-gray-100 rounded text-gray-500">[Student Last Name]</div>
                        </div>
                        <div>
                            <span class="label">Class</span>
                            <div class="p-2 bg-gray-100 rounded text-gray-500">[Student Class]</div>
                        </div>

                        <div class="space-y-2">
                            <span class="label">Available Internships</span>
                            <div id="internship-template-list" class="space-y-2">
                                <p class="text-gray-500 text-sm">No internships added yet</p>
                            </div>

                            <div class="flex gap-2">
                                <input class="input flex-1" id="new-internship-field" type="text" placeholder="Enter internship name">
                                <button onclick="addInternshipToTemplate()" class="button-blue">+</button>
                            </div>
                        </div>

                        <button onclick="saveInternshipTemplate()" class="button w-full">
                            Save Template
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Global state
        let currentView = 'initial';
        let students = [];
        let currentStudent = null;
        let selectedClass = '';
        let selectedStudentForView = null;
        let internshipTemplate = [];
        let tempSelectedInternships = [];
        let showRegister = false;
        let showInternships = false;

        // Utility functions
        function showView(viewName) {
            // Hide all views
            const views = document.querySelectorAll('[id$="-view"]');
            views.forEach(view => view.classList.add('hidden'));

            // Show selected view
            const targetView = document.getElementById(viewName + '-view');
            if (targetView) {
                targetView.classList.remove('hidden');
                currentView = viewName;
            }
        }

        function toggleAuthMode() {
            showRegister = !showRegister;
            const registerButton = document.getElementById('register-button');
            const loginButton = document.getElementById('login-button');
            const toggleText = document.getElementById('auth-toggle-text');

            if (showRegister) {
                registerButton.classList.remove('hidden');
                loginButton.classList.add('hidden');
                toggleText.textContent = 'Already have an account? Log In';
            } else {
                registerButton.classList.add('hidden');
                loginButton.classList.remove('hidden');
                toggleText.textContent = 'Need an account? Register';
            }
        }

        function toggleInternshipsDisplay() {
            showInternships = !showInternships;
            const display = document.getElementById('internships-display');
            const icon = document.getElementById('chevron-icon');

            if (showInternships) {
                display.classList.remove('hidden');
                icon.textContent = '▲';
            } else {
                display.classList.add('hidden');
                icon.textContent = '▼';
            }
        }

        // Student functions
        function handleStudentRegister() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;

            if (username.trim() && password.length >= 8) {
                const newStudent = {
                    username,
                    password,
                    selectedInternships: [],
                    cardSubmitted: false
                };
                students.push(newStudent);
                currentStudent = newStudent;

                // Clear form
                document.getElementById('username').value = '';
                document.getElementById('password').value = '';

                showView('student-card');
                updateStudentCard();
            } else {
                alert('Username required and password must be at least 8 characters');
            }
        }

        function handleStudentLogin() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;

            const student = students.find(s => s.username === username && s.password === password);
            if (student) {
                currentStudent = student;

                // Populate form
                document.getElementById('firstName').value = student.firstName || '';
                document.getElementById('lastName').value = student.lastName || '';
                document.getElementById('studentClass').value = student.class || '';

                // Clear login form
                document.getElementById('username').value = '';
                document.getElementById('password').value = '';

                showView('student-card');
                updateStudentCard();
            } else {
                alert('Invalid username or password');
            }
        }

        function updateStudentCard() {
            const internshipsSection = document.getElementById('internships-section');
            if (internshipTemplate.length > 0) {
                internshipsSection.classList.remove('hidden');
                updateAvailableInternships();
                updateSelectedInternshipsDisplay();
            } else {
                internshipsSection.classList.add('hidden');
            }
        }

        function updateAvailableInternships() {
            const container = document.getElementById('available-internships');
            container.innerHTML = '';

            internshipTemplate.forEach(internship => {
                const div = document.createElement('div');
                div.className = 'available-internship';
                div.textContent = internship;
                container.appendChild(div);
            });
        }

        function updateSelectedInternshipsDisplay() {
            const container = document.getElementById('selected-internships-display');
            const list = document.getElementById('selected-internships-list');

            if (currentStudent?.selectedInternships && currentStudent.selectedInternships.length > 0) {
                container.classList.remove('hidden');
                list.innerHTML = '';

                currentStudent.selectedInternships.forEach(internship => {
                    const div = document.createElement('div');
                    div.className = 'selected-internship';
                    div.textContent = '✓ ' + internship;
                    list.appendChild(div);
                });
            } else {
                container.classList.add('hidden');
            }
        }

        function handleStudentCardSubmit() {
            const firstName = document.getElementById('firstName').value;
            const lastName = document.getElementById('lastName').value;
            const studentClass = document.getElementById('studentClass').value;

            if (currentStudent && firstName.trim() && lastName.trim() && studentClass.trim()) {
                // Update student data
                const studentIndex = students.findIndex(s => s.username === currentStudent.username);
                if (studentIndex !== -1) {
                    students[studentIndex] = {
                        ...students[studentIndex],
                        firstName,
                        lastName,
                        class: studentClass,
                        cardSubmitted: true
                    };
                    currentStudent = students[studentIndex];
                }

                alert('Student card submitted successfully!');
            } else {
                alert('Please fill in all fields');
            }
        }

        function updateInternshipCheckboxes() {
            const container = document.getElementById('internship-checkboxes');
            container.innerHTML = '';

            internshipTemplate.forEach((internship, index) => {
                const div = document.createElement('div');
                div.className = 'checkbox-container';

                const checkbox = document.createElement('input');
                checkbox.type = 'checkbox';
                checkbox.id = `internship-${index}`;
                checkbox.className = 'checkbox';
                checkbox.checked = tempSelectedInternships.includes(internship);
                checkbox.onchange = () => toggleInternshipSelection(internship);

                const label = document.createElement('label');
                label.htmlFor = `internship-${index}`;
                label.className = 'text-sm cursor-pointer flex-1';
                label.textContent = internship;

                div.appendChild(checkbox);
                div.appendChild(label);
                container.appendChild(div);
            });
        }

        function toggleInternshipSelection(internship) {
            if (tempSelectedInternships.includes(internship)) {
                tempSelectedInternships = tempSelectedInternships.filter(i => i !== internship);
            } else {
                tempSelectedInternships.push(internship);
            }

            // Update save button text
            document.getElementById('save-button-text').textContent =
                `Save Selections (${tempSelectedInternships.length})`;
        }

        function saveInternshipSelections() {
            if (currentStudent) {
                const studentIndex = students.findIndex(s => s.username === currentStudent.username);
                if (studentIndex !== -1) {
                    students[studentIndex].selectedInternships = [...tempSelectedInternships];
                    currentStudent = students[studentIndex];
                }

                showView('student-card');
                updateStudentCard();
                alert('Internship selections saved!');
            }
        }

        // Admin functions
        function handleAdminLogin() {
            const password = document.getElementById('adminPassword').value;

            if (password === 'DimaIsTheGod') {
                document.getElementById('adminPassword').value = '';
                showView('admin-dashboard');
            } else {
                alert('Incorrect administrator password');
            }
        }

        function getSubmittedStudents() {
            return students
                .filter(s => s.cardSubmitted && s.lastName)
                .sort((a, b) => a.lastName.localeCompare(b.lastName));
        }

        function getUniqueClasses() {
            const classes = students
                .filter(s => s.cardSubmitted && s.class)
                .map(s => s.class)
                .filter((value, index, self) => self.indexOf(value) === index)
                .sort((a, b) => {
                    const numA = parseInt(a);
                    const numB = parseInt(b);
                    if (!isNaN(numA) && !isNaN(numB)) {
                        return numA - numB;
                    }
                    return a.localeCompare(b);
                });
            return classes;
        }

        function getStudentsByClass(className) {
            return students
                .filter(s => s.cardSubmitted && s.class === className && s.lastName)
                .sort((a, b) => a.lastName.localeCompare(b.lastName));
        }

        function updateClassesList() {
            const container = document.getElementById('classes-list');
            const classes = getUniqueClasses();

            container.innerHTML = '';

            if (classes.length === 0) {
                const p = document.createElement('p');
                p.className = 'text-white opacity-75 text-center';
                p.textContent = 'No classes found';
                container.appendChild(p);
            } else {
                classes.forEach(className => {
                    const card = document.createElement('div');
                    card.className = 'card student-card';
                    card.onclick = () => {
                        selectedClass = className;
                        document.getElementById('selected-class-name').textContent = className;
                        updateStudentsByClassList();
                        showView('admin-students-by-class');
                    };

                    const h3 = document.createElement('h3');
                    h3.textContent = `Class ${className}`;

                    const p = document.createElement('p');
                    p.textContent = `${getStudentsByClass(className).length} students`;

                    card.appendChild(h3);
                    card.appendChild(p);
                    container.appendChild(card);
                });
            }
        }

        function updateStudentsByClassList() {
            const container = document.getElementById('students-by-class-list');
            const classStudents = getStudentsByClass(selectedClass);

            container.innerHTML = '';

            classStudents.forEach(student => {
                const card = document.createElement('div');
                card.className = 'card student-card';
                card.onclick = () => {
                    selectedStudentForView = student;
                    updateStudentCardView();
                    showView('admin-view-student-card');
                };

                const h3 = document.createElement('h3');
                h3.textContent = `${student.lastName}, ${student.firstName}`;

                const p1 = document.createElement('p');
                p1.textContent = `Username: ${student.username}`;

                card.appendChild(h3);
                card.appendChild(p1);

                if (student.selectedInternships && student.selectedInternships.length > 0) {
                    const p2 = document.createElement('p');
                    p2.textContent = `Selected Internships: ${student.selectedInternships.length}`;
                    card.appendChild(p2);
                }

                container.appendChild(card);
            });
        }

        function updateStudentCardView() {
            if (!selectedStudentForView) return;

            document.getElementById('view-firstName').textContent = selectedStudentForView.firstName;
            document.getElementById('view-lastName').textContent = selectedStudentForView.lastName;
            document.getElementById('view-class').textContent = selectedStudentForView.class;

            // Available internships
            const availableSection = document.getElementById('view-available-internships');
            const availableList = document.getElementById('view-available-internships-list');

            if (internshipTemplate.length > 0) {
                availableSection.classList.remove('hidden');
                availableList.innerHTML = '';

                internshipTemplate.forEach(internship => {
                    const div = document.createElement('div');
                    div.className = 'available-internship';
                    div.textContent = internship;
                    availableList.appendChild(div);
                });
            } else {
                availableSection.classList.add('hidden');
            }

            // Selected internships
            const selectedSection = document.getElementById('view-selected-internships');
            const selectedList = document.getElementById('view-selected-internships-list');

            if (selectedStudentForView.selectedInternships && selectedStudentForView.selectedInternships.length > 0) {
                selectedSection.classList.remove('hidden');
                selectedList.innerHTML = '';

                selectedStudentForView.selectedInternships.forEach(internship => {
                    const div = document.createElement('div');
                    div.className = 'selected-internship';
                    div.textContent = '✓ ' + internship;
                    selectedList.appendChild(div);
                });
            } else {
                selectedSection.classList.add('hidden');
            }
        }

        function updateInternshipTemplateList() {
            const container = document.getElementById('internship-template-list');
            container.innerHTML = '';

            if (internshipTemplate.length === 0) {
                const p = document.createElement('p');
                p.className = 'text-gray-500 text-sm';
                p.textContent = 'No internships added yet';
                container.appendChild(p);
            } else {
                internshipTemplate.forEach((internship, index) => {
                    const div = document.createElement('div');
                    div.className = 'internship-item';

                    const span = document.createElement('span');
                    span.className = 'text-sm';
                    span.textContent = internship;

                    const button = document.createElement('button');
                    button.className = 'remove-button';
                    button.textContent = '✕';
                    button.onclick = () => removeInternshipFromTemplate(index);

                    div.appendChild(span);
                    div.appendChild(button);
                    container.appendChild(div);
                });
            }
        }

        function addInternshipToTemplate() {
            const input = document.getElementById('new-internship-field');
            const value = input.value.trim();

            if (value) {
                internshipTemplate.push(value);
                input.value = '';
                updateInternshipTemplateList();
            }
        }

        function removeInternshipFromTemplate(index) {
            internshipTemplate.splice(index, 1);
            updateInternshipTemplateList();
        }

        function saveInternshipTemplate() {
            alert('Internship template saved! All student cards will now show these internships.');
            showView('admin-dashboard');
        }

        // Event listeners and initialization
        document.addEventListener('DOMContentLoaded', function() {
            // Initialize auth mode
            toggleAuthMode();

            // Add enter key listeners
            document.getElementById('adminPassword').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    handleAdminLogin();
                }
            });

            document.getElementById('new-internship-field').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    addInternshipToTemplate();
                }
            });
        });

        // Override showView for special cases
        const originalShowView = showView;
        showView = function(viewName) {
            if (viewName === 'admin-classes') {
                updateClassesList();
            } else if (viewName === 'student-select-internships') {
                tempSelectedInternships = currentStudent?.selectedInternships ? [...currentStudent.selectedInternships] : [];
                updateInternshipCheckboxes();
                document.getElementById('save-button-text').textContent =
                    `Save Selections (${tempSelectedInternships.length})`;
            } else if (viewName === 'admin-add-internships') {
                updateInternshipTemplateList();
            }

            originalShowView(viewName);
        };
    </script>
</body>
</html>

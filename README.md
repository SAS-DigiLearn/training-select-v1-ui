# SAS Role Specific Learning Dashboard

1. Project Purpose
This dashboard is a client-side web application that dynamically displays role-specific learning
content. The system reads structured CSV data, maps roles to courses, and renders a VLE-style
interface for users to launch training and track completion status using browser localStorage.

2. Technology Stack
• HTML5 – structure and layout
• CSS3 – styling and responsive layout
• Vanilla JavaScript – application logic
• PapaParse (CDN) – CSV parsing
• Browser localStorage – persistence layer

3. Data Architecture
The application relies on three CSV datasets:
• courses.csv – defines learning resources
• roles.csv – defines organisational hierarchy
• role_course_map.csv – many-to-many mapping between roles and courses

4. Application Flow
• Page loads
• CSV files fetched asynchronously using Promise.all()
• CSV parsed into arrays using PapaParse
• Departments populated from roles dataset
• User selects Department → Area → Role
• Mapped course IDs retrieved
• Course cards dynamically generated
• Completion status retrieved from localStorage

5. Key JavaScript Components
Data Loading
Promise.all() retrieves CSV files concurrently. Papa.parse converts CSV text into structured
JavaScript objects.
Dynamic Filtering
Dropdown selections filter rolesData to progressively narrow available options. Filtering uses array
methods such as filter() and map().
DOM Rendering
Course cards are generated dynamically using document.createElement(). innerHTML templates
populate title, badge type, launch button and completion toggle.
Completion Tracking
Each toggle writes a status value to localStorage using a composite key: roleID_courseID This
ensures completion tracking is unique per role.
Favourite Role Persistence
Favourite role is stored using localStorage key 'favouriteRole'. The interface updates dynamically to
reflect saved selections.

6. Storage Model
• selectedDepartment
• selectedArea
• selectedRole
• favouriteRole
• roleID_courseID completion flags

7. UI Behaviour Logic
• Buttons conditionally shown depending on role selection state
• Saved role auto-load uses timed dispatch events
• Completion toggles update UI text dynamically
• Cards render differently depending on course category

8. Security Considerations
• No server-side processing
• No authentication layer
• No external data persistence
• Links open in new browser tab using window.open()

9. Scalability Considerations
• CSV structure supports unlimited roles
• Course mapping supports many-to-many relationships
• Modular functions allow extension
• UI grid auto-adjusts using CSS grid

10. Potential Enhancements
• API integration instead of CSV
• User authentication
• Progress analytics dashboard
• Multi-role selection
• Search and tagging functionality

// Smooth scrolling for navigation links
document.querySelectorAll('nav ul li a').forEach(anchor => {
    anchor.addEventListener('click', function (e) {
        e.preventDefault(); // Prevent default jump behavior

        const targetId = this.getAttribute('href'); // Get the href value (e.g., "#about")
        const targetSection = document.querySelector(targetId); // Find the section

        if (targetSection) {
            window.scrollTo({
                top: targetSection.offsetTop - document.querySelector('header').offsetHeight, // Adjust for fixed header
                behavior: 'smooth' // Smooth scroll effect
            });
        }
    });
});

// Menu Tab Functionality
document.addEventListener('DOMContentLoaded', () => {
    const tabButtons = document.querySelectorAll('.tab-button');
    const menuCategories = document.querySelectorAll('.menu-category');

    tabButtons.forEach(button => {
        button.addEventListener('click', () => {
            // Remove active class from all buttons and categories
            tabButtons.forEach(btn => btn.classList.remove('active'));
            menuCategories.forEach(category => category.classList.remove('active-category'));

            // Add active class to the clicked button
            button.classList.add('active');

            // Get the category ID from the data-category attribute
            const categoryId = button.dataset.category;

            // Show the corresponding menu category
            document.getElementById(categoryId).classList.add('active-category');
        });
    });

    // Optionally activate the first tab by default on page load
    if (tabButtons.length > 0) {
        tabButtons[0].click();
    }
});
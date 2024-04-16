document.addEventListener('DOMContentLoaded', () => {
  const navLinks = document.querySelectorAll('.navbar a');
  const currentPath = window.location.pathname.split('/').pop(); // Gets only the filename, assuming it matches your href exactly.

  navLinks.forEach(link => {
      // Remove the current-page class from all links
      link.classList.remove('current-page');

      // Check if the link's href matches the current filename
      if (link.getAttribute('href') === currentPath) {
          link.classList.add('current-page');
          // Ensure the active indicator is within the same parent div for proper styling
          const activeIndicator = document.createElement('div');
          activeIndicator.className = 'active-indicator';
          activeIndicator.style.visibility = 'visible'; // Make sure it's visible
          link.parentElement.appendChild(activeIndicator); // Append to the parent of the link

          // Update underline position and width to match active link
          activeIndicator.style.width = `${link.offsetWidth}px`;
          activeIndicator.style.left = `${link.offsetLeft}px`;
      }
  });
});
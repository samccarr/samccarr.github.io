// js to add 'current-page' class to the active link and update underline position
document.addEventListener('DOMContentLoaded', () => {
    const navLinks = document.querySelectorAll('.navbar a');
    const activeIndicator = document.createElement('div');
    activeIndicator.className = 'active-indicator';
    document.querySelector('.navbar').appendChild(activeIndicator);
  
    function updateActiveLink(currentActiveLink) {
      // remove 'current-page' class from all links
      navLinks.forEach(link => link.classList.remove('current-page'));
  
      // Add 'current-page' class to the clicked link
      currentActiveLink.classList.add('current-page');
  
      // update underline position and width to match active link
      activeIndicator.style.width = `${currentActiveLink.offsetWidth}px`;
      activeIndicator.style.left = `${currentActiveLink.offsetLeft}px`;
      activeIndicator.style.transform = 'none'; // Reset transform for initial positioning
    }
  
    // set initial position of the underline
    const initialActiveLink = document.querySelector('.navbar .current-page');
    if (initialActiveLink) {
      updateActiveLink(initialActiveLink);
    }
  
    // attach click event listeners to nav links
    navLinks.forEach(link => {
      link.addEventListener('click', (event) => {
        event.preventDefault(); // prevent default link behavior
        updateActiveLink(event.currentTarget);
      });
    });
  });
  

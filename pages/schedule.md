---
layout: page
title: Programme
toc: true
---

**On this page:** 
* [Schedule](#schedule)
* [Book of Abstracts](#book-of-abstracts)


<h2 id="schedule">Schedule</h2>

Schedule will be updated regularly. Latest version: 01 July, 2025. 

Your viewing options:

1.  <a href="/2025/IACAP-AISB_Program_2025-07-01.pdf">PDF download</a> optimised for printing.

2. Interactive web content optimised for screen and mobile viewing:

{% include schedule.html %}

<h2 id="book-of-abstracts">Book of Abstracts</h2>

 A booklet with abstracts of all talks and posters, with two viewing options:

 1.   <a href="/2025/IACAP-AISB-2025_Book_of_Abstracts.pdf">PDF download</a> optimised for printing.

 2. Interactive web content optimised for screen and mobile viewing:

<!-- <object data="/2025/IACAP-AISB-2025_Book_of_Abstracts.pdf" width="100%" height="1100"></object>  -->

{% include abstracts-toc.html %}


{% include abstracts-accordion.html %}

<script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>
<script src="https://code.jquery.com/ui/1.14.1/jquery-ui.min.js"></script>
<link rel="stylesheet" href="https://code.jquery.com/ui/1.14.1/themes/base/jquery-ui.css">


<script>
$(document).ready(function() {
// Show loading indicator while initializing
$('body').addClass('loading');

// Initialize main accordion for days
$("#mainAccordion").accordion({
header: "> h3",
heightStyle: "content",
collapsible: true,
active: 1, // Open first day by default
animate: 300,
icons: {
header: "ui-icon-triangle-1-e",
activeHeader: "ui-icon-triangle-1-s"
}
});

// Initialize all track accordions
$(".tracks-accordion").each(function() {
$(this).accordion({
header: "> h3",
heightStyle: "content",
collapsible: true,
active: false, // Start with all tracks collapsed
animate: 200,
icons: {
header: "ui-icon-triangle-1-e",
activeHeader: "ui-icon-triangle-1-s"
}
});
});

// Abstract toggle functionality
$('.abstract-toggle').click(function(e) {
e.stopPropagation();
var $this = $(this);
var abstractId = $this.data('abstract-id');
var $abstract = $('#' + abstractId);

if ($abstract.is(':visible')) {
$abstract.slideUp(200);
$this.html('View Abstract ▼');
} else {
$abstract.slideDown(200);
$this.html('Hide Abstract ▲');
}
});

// Initialize abstracts accordion
$("#abstractsAccordion").accordion({
  header: "> h3",
  heightStyle: "content",
  collapsible: true,
  active: false, // Start with all sections collapsed
  animate: 300,
  icons: {
    header: "ui-icon-triangle-1-e",
    activeHeader: "ui-icon-triangle-1-s"
  }
});

// Initialize symposia nested accordions
$(".symposia-accordion").each(function() {
  $(this).accordion({
    header: "> h3",
    heightStyle: "content",
    collapsible: true,
    active: false,
    animate: 200,
    icons: {
      header: "ui-icon-triangle-1-e",
      activeHeader: "ui-icon-triangle-1-s"
    }
  });
}); 

// ToC navigation for abstracts
$('.toc-link').click(function(e) {
  e.preventDefault();
  
  var targetId = $(this).attr('href').substring(1);
  var $target = $('#' + targetId);
  var section = $(this).data('section');
  var symposiumId = $(this).data('symposium');
  
  // Open the appropriate accordion section
  var $mainAccordion = $("#abstractsAccordion");
  var sectionIndex = $mainAccordion.find('> h3').index($('#' + section));
  $mainAccordion.accordion("option", "active", sectionIndex);
  
  // If it's in a symposium, open that too
  if (symposiumId) {
    setTimeout(function() {
      var $sympAccordion = $(".symposia-accordion");
      var sympIndex = $sympAccordion.find('> h3').index($('#' + symposiumId));
      $sympAccordion.accordion("option", "active", sympIndex);
      
      // Scroll to the talk after accordions open
      setTimeout(function() {
        $('html, body').animate({
          scrollTop: $target.offset().top - 100
        }, 500);
        
        // Highlight the talk
        $target.addClass('highlighted');
        setTimeout(function() {
          $target.removeClass('highlighted');
        }, 2000);
      }, 400);
    }, 400);
  } else {
    // Scroll to the talk after accordion opens
    setTimeout(function() {
      $('html, body').animate({
        scrollTop: $target.offset().top - 100
      }, 500);
      
      // Highlight the talk
      $target.addClass('highlighted');
      setTimeout(function() {
        $target.removeClass('highlighted');
      }, 2000);
    }, 400);
  }
});

// Remove loading indicator
$('body').removeClass('loading');
});



</script>

<head>
<style>


.version {
text-align: center;
color: #666;
margin-bottom: 20px;
font-size: 0.9rem;
}

/* jQuery UI Accordion Overrides - Main Level (Days) */
#mainAccordion.ui-accordion .ui-accordion-header {
background: #34495e;
color: white;
border: none;
border-radius: 8px;
margin-bottom: 5px;
padding: 15px 20px;
font-size: 1.1rem;
font-weight: bold;
cursor: pointer;
transition: background 0.3s;
}

#mainAccordion.ui-accordion .ui-accordion-header:hover {
background: #2c3e50;
}

#mainAccordion.ui-accordion .ui-accordion-header.ui-state-active {
background: #2c3e50;
border-radius: 8px 8px 0 0;
margin-bottom: 0;
}

#mainAccordion.ui-accordion .ui-accordion-content {
background: white;
border: none;
padding: 20px;
margin-bottom: 5px;
border-radius: 0 0 8px 8px;
box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

/* jQuery UI Icons for main accordion */
#mainAccordion .ui-icon {
background-image: none !important;
text-indent: 0;
position: absolute;
right: 20px;
top: 50%;
transform: translateY(-50%);
width: auto;
height: auto;
font-size: 1.5rem;
margin-top: 0;
}

#mainAccordion .ui-icon:before {
content: "+";
color: white;
font-weight: bold;
}

#mainAccordion .ui-state-active .ui-icon:before {
content: "−";
}

/* Session styles */
.session {
margin-bottom: 20px;
padding: 15px;
background: #f8f9fa;
border-radius: 8px;
border-left: 4px solid #3498db;
}

.session-break {
border-left-color: #f39c12;
background: #fef5e7;
}

.session-plenary {
border-left-color: #27ae60;
background: #e8f8f5;
text-color: #000;
}

.session-special, .session-social {
border-left-color: #9b59b6;
background: #f4ecf7;
}

.session-registration {
border-left-color: #95a5a6;
background: #ecf0f1;
}

.session-closing {
border-left-color: #e74c3c;
background: #fadbd8;
}

.session-time {
font-weight: bold;
color: #2c3e50;
font-size: 1.1rem;
margin-bottom: 5px;
}

.session-title {
font-weight: 500;
margin-bottom: 10px;
}

.plenary-info {
margin-top: 10px;
padding: 10px;
background: white;
border-radius: 4px;
}

.plenary-title {
font-size: 1.1rem;
font-weight: 600;
color: #2c3e50;
margin-bottom: 8px;
}

.plenary-speaker {
font-weight: bold;
color: #27ae60;
}

.plenary-chair {
font-size: 0.9rem;
color: #666;
margin-top: 5px;
}

/* Track accordion styles (nested) */
.tracks-accordion.ui-accordion {
margin-top: 15px;
}

.tracks-accordion.ui-accordion .ui-accordion-header {
background: #ecf0f1;
color: #2c3e50;
border: 1px solid #ddd;
border-radius: 4px;
margin-bottom: 8px;
padding: 12px 15px;
font-size: 0.95rem;
font-weight: 500;
cursor: pointer;
transition: all 0.2s;
position: relative;
}

.tracks-accordion.ui-accordion .ui-accordion-header:hover {
background: #d5dbdb;
border-color: #bdc3c7;
}

.tracks-accordion.ui-accordion .ui-accordion-header.ui-state-active {
background: #3498db;
color: white;
border-color: #3498db;
border-radius: 4px 4px 0 0;
margin-bottom: 0;
}

.tracks-accordion.ui-accordion .ui-accordion-content {
background: white;
border: 1px solid #ddd;
border-top: none;
padding: 15px;
margin-bottom: 8px;
border-radius: 0 0 4px 4px;
}

/* Track type indicators */
.tracks-accordion .track-type-symposium {
background: #495e34 !important;
}

.tracks-accordion .track-type-workshop {
background: #5e3449 !important;
}

/* Icons for track accordion */
.tracks-accordion .ui-icon {
background-image: none !important;
text-indent: 0;
position: absolute;
right: 15px;
top: 50%;
transform: translateY(-50%);
width: auto;
height: auto;
font-size: 1.2rem;
margin-top: 0;
}

.tracks-accordion .ui-icon:before {
content: "▶";
color: #7f8c8d;
font-size: 0.8rem;
}

.tracks-accordion .ui-state-active .ui-icon:before {
content: "▼";
color: white;
}

/* Talk styles */
.talk-item {
margin-bottom: 12px;
padding: 10px;
background: #f8f9fa;
border-radius: 4px;
border-left: 3px solid #3498db;
}

.talk-time {
font-size: 0.85rem;
color: #7f8c8d;
font-weight: 500;
}

.talk-title {
font-weight: 500;
margin: 3px 0;
color: #2c3e50;
}

.talk-speakers {
font-size: 0.9rem;
color: #666;
font-style: italic;
}

/* Abstract toggle styles */
.abstract-toggle {
margin-top: 5px;
color: #3498db;
font-size: 0.85rem;
cursor: pointer;
display: inline-block;
user-select: none;
transition: color 0.2s;
}

.abstract-toggle:hover {
color: #2980b9;
text-decoration: underline;
}

.talk-abstract {
display: none;
margin-top: 10px;
padding: 10px;
background: white;
border-radius: 4px;
border: 1px solid #e0e0e0;
font-size: 0.9rem;
line-height: 1.5;
}

.talk-abstract p {
margin: 0 0 10px 0;
}

.talk-abstract p:last-child {
margin-bottom: 0;
}

.no-talks {
color: #999;
font-style: italic;
font-size: 0.9rem;
padding: 10px;
}

/* Remove default jQuery UI focus outlines */
.ui-accordion .ui-accordion-header:focus {
outline: none;
box-shadow: 0 0 0 2px rgba(52, 152, 219, 0.3);
}

/* Loading indicator */
.loading {
text-align: center;
padding: 40px;
color: #666;
}

/* Disable abstracts toggle */
.abstracts-disabled .abstract-toggle {
display: none;
}


#mainAccordion.ui-accordion .ui-accordion-header {
padding: 12px 40px 12px 15px;
font-size: 1rem;
}

#mainAccordion .ui-icon {
right: 10px;
}

.session { padding: 12px; }

.tracks-accordion.ui-accordion .ui-accordion-header {
padding: 10px 35px 10px 12px;
font-size: 0.9rem;
}

.tracks-accordion .ui-icon {
right: 10px;
} 


/* Abstracts Accordion Styles */
#abstractsAccordion.ui-accordion .ui-accordion-header {
  background: #34495e;
  color: white;
  border: none;
  border-radius: 8px;
  margin-bottom: 5px;
  padding: 15px 20px;
  font-size: 1.1rem;
  font-weight: bold;
  cursor: pointer;
  transition: background 0.3s;
}

#abstractsAccordion.ui-accordion .ui-accordion-header:hover {
  background: #2c3e50;
}

#abstractsAccordion.ui-accordion .ui-accordion-header.ui-state-active {
  background: #2c3e50;
  border-radius: 8px 8px 0 0;
  margin-bottom: 0;
}

#abstractsAccordion.ui-accordion .ui-accordion-content {
  background: white;
  border: none;
  padding: 20px;
  margin-bottom: 5px;
  border-radius: 0 0 8px 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

/* Icons for abstracts accordion */
#abstractsAccordion .ui-icon {
  background-image: none !important;
  text-indent: 0;
  position: absolute;
  right: 20px;
  top: 50%;
  transform: translateY(-50%);
  width: auto;
  height: auto;
  font-size: 1.5rem;
  margin-top: 0;
}

#abstractsAccordion .ui-icon:before {
  content: "+";
  color: white;
  font-weight: bold;
}

#abstractsAccordion .ui-state-active .ui-icon:before {
  content: "−";
}

/* Symposia nested accordion */
.symposia-accordion.ui-accordion .ui-accordion-header {
  background: #ecf0f1;
  color: #2c3e50;
  border: 1px solid #ddd;
  border-radius: 4px;
  margin-bottom: 8px;
  padding: 12px 15px;
  font-size: 0.95rem;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
}

.symposia-accordion.ui-accordion .ui-accordion-header:hover {
  background: #d5dbdb;
  border-color: #bdc3c7;
}

.symposia-accordion.ui-accordion .ui-accordion-header.ui-state-active {
  background: #3498db;
  color: white;
  border-color: #3498db;
  border-radius: 4px 4px 0 0;
  margin-bottom: 0;
}

/* Talk item styles for abstracts */
.talk-item {
  margin-bottom: 20px;
  padding: 15px;
  background: #f8f9fa;
  border-radius: 4px;
  border-left: 3px solid #3498db;
}

.talk-item h4 {
  margin-top: 0;
  color: #2c3e50;
}

.talk-speakers {
  font-weight: bold;
  color: #666;
  margin: 5px 0;
  font-style: italic;
}

.talk-item p{
  margin-top: 10px;
  line-height: 1.6;
}

.talk-item p {
  margin: 10px 0;
}

.talk-item p:first-child {
  margin-top: 0;
}

.talk-item p:last-child {
  margin-bottom: 0;
}

/* Section-specific colors */
.section-plenary .talk-item {
  border-left-color: #27ae60;
  background: #e8f8f5;
}

.section-poster .talk-item {
  border-left-color: #f39c12;
  background: #fef5e7;
}

.symposium-content {
  padding: 10px 0;
}

/* Table of Contents styles */
.abstracts-toc {
  background: #f8f9fa;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 20px;
  margin-bottom: 30px;
}

.abstracts-toc h3 {
  margin-top: 0;
  color: #2c3e50;
}

.toc-section {
  margin-bottom: 20px;
}

.toc-section h4 {
  color: #34495e;
  margin-bottom: 10px;
}

.toc-symposium {
  margin-left: 20px;
  margin-bottom: 15px;
}

.toc-symposium h5 {
  color: #3498db;
  margin-bottom: 8px;
}

.abstracts-toc ul {
  list-style: none;
  padding-left: 0;
}

.abstracts-toc li {
  margin-bottom: 8px;
}

.toc-link {
  display: block;
  text-decoration: none;
  padding: 5px 10px;
  border-radius: 4px;
  transition: background 0.2s;
}

.toc-link:hover {
  background: #e8f4f8;
}

.toc-title {
  display: block;
  color: #2c3e50;
  font-weight: 500;
}

.toc-authors {
  display: block;
  color: #666;
  font-size: 0.9em;
  font-style: italic;
}

/* Highlight effect */
.talk-item.highlighted {
  animation: highlight 2s ease-out;
}

@keyframes highlight {
  0% {
    background-color: #fff3cd;
    transform: scale(1.02);
  }
  100% {
    background-color: inherit;
    transform: scale(1);
  }
}
</style>
</head>
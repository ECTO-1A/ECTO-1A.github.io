# Current Projects Page - Quick Add Instructions

## How to Add a New Day/Project Entry

### Method 1: Add to Existing Day
If you want to add a project to an existing day, just add a new `project-item` div within that day's section:

```html
<div class="project-item">
    <div class="project-date">July 3rd, 2025</div>
    <h3 class="project-title">Your Project Title</h3>
    <div class="project-description">
        <p>Your project description here...</p>
    </div>
</div>
```

### Method 2: Add a New Day
To add a completely new day, copy this template and paste it at the top of the projects-content section (after line 17):

```html
<div class="day-section">
    <div class="day-header">
        <h2 class="day-title">NEW_DATE_HERE</h2>
    </div>
    
    <div class="project-item">
        <div class="project-date">NEW_DATE_HERE</div>
        <h3 class="project-title">PROJECT_TITLE_HERE</h3>
        <div class="project-description">
            <p>PROJECT_DESCRIPTION_HERE</p>
        </div>
    </div>
</div>
```

### Optional Elements You Can Add:

#### Add an Image:
```html
<div class="project-image">
    <img src="/assets/images/your-image.png" alt="Description" width="450" style="border: 5px solid black; display: block; margin-left: auto; margin-right: auto;">
</div>
```

#### Add a Video:
```html
<div class="project-media">
    <h4>Related Video:</h4>
    <div class="video-container">
        <iframe src="YOUR_VIDEO_URL" title="Video title" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    </div>
</div>
```

## Quick Steps:
1. Open `_pages/Current Projects.md`
2. Find the `projects-content` section (around line 17)
3. Copy the template above
4. Replace `NEW_DATE_HERE`, `PROJECT_TITLE_HERE`, and `PROJECT_DESCRIPTION_HERE`
5. Add optional images/videos if needed
6. Save the file

## Tips:
- Always add new days at the TOP of the projects-content section for chronological order
- Each project gets its own date stamp for easy tracking
- The day sections are visually separated with a green left border
- Images and videos are optional but enhance the presentation

## Current Structure:
- Header with date range and last updated
- Day sections (grouped by date)
- Individual projects within each day
- Each project shows its specific date

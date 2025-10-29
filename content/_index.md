---
# Leave the homepage title empty to use the site title
title: ""
date: 2022-10-24
type: landing

design:
  # Default section spacing
  spacing: "6rem"

sections:
  - block: resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
      text: ""
      # Show a call-to-action button under your biography? (optional)
      button:
        text: Download CV
        url: uploads/resume.pdf?v=20251029
      headings:
        about: ""
        education: ""
        interests: ""
    design:
      # Apply a gradient background
      css_class: hbx-bg-gradient
      # Avatar customization
      avatar:
        size: xl # Options: small (150px), medium (200px, default), large (320px), xl (400px), xxl (500px)
        shape: circle # Options: circle (default), square, rounded
  - block: markdown
    content:
      title: "📚 My Research"
      subtitle: ""
      text: |-
        I'm a master student, looking the best way to make a positive impact on the world, wether it its in acadmeia or in industry. 

        I apply control methods to make machine able to adapt do the uncertaintiy of the world, and reliably execute task.

        I'm always happ to talk to people, just reach out 😃
    design:
      columns: "1"
  - block: collection
    id: papers
    content:
      title: Featured Publications
      filters:
        folders:
          - publications
        publication_type: "paper-conference"
        featured_only: true
      # Show only one featured publication
      count: 1
    design:
      view: article-grid
      columns: 1
  # Removed 'Recent Publications' block as requested
  - block: collection
    id: Recent Projects
    content:
      title: Projects
      subtitle: ""
      text: ""
      # Page type to display. E.g. post, talk, publication...
      page_type: projects
      # Choose how many pages you would like to display (0 = all pages)
      count: 2
      # Filter on criteria
      filters:
        author: ""
        category: ""
        tag: ""
        exclude_featured: false
        exclude_future: false
        exclude_past: false
        publication_type: ""
      # Choose how many pages you would like to offset by
      offset: 0
      # Page order: descending (desc) or ascending (asc) date.
      order: desc
    design:
      # Choose a layout view
      view: card
      # Reduce spacing
      spacing:
        padding: [0, 0, 0, 0]
---

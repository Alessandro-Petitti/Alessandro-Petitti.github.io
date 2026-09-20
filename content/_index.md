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
        url: uploads/resume.pdf
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
        I'm a master student in robotics at ETH Zürich, looking for the best way to make a positive impact on the world, whether in academia or in industry.

        I apply optimization-based control methods to make machines adapt to the uncertainty of the world and reliably execute tasks. My work spans model predictive control for agile flight, soft robotics, and learning for manipulation.

        **Right now:** I'm starting my master thesis at the Soft Robotics Lab (ETH Zürich), on using high-fidelity simulation of soft objects as a supervision engine to learn manipulation policies that transfer to a real Franka robot.

        I'm always happy to talk to people, just reach out 😃
    design:
      columns: "1"
  - block: collection
    id: papers
    content:
      title: Featured Publications
      filters:
        folders:
          - publications
        featured_only: true
      # Show the featured publications
      count: 2
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

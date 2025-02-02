---
# Leave the homepage title empty to use the site title
title: ""
date: 2025-01-14
type: landing

design:
  # Default section spacing
  spacing: "6rem"

sections:
  - block: resume-biography-3
    content:
      # Choose a user profile to display (a folder name within content/authors/)
      username: admin
      text: ""
      button:
        text: Download CV
        url: https://www.canva.com/design/DAGcq4nJg20/Wmn-2Q6jBE-xiP9VUfHNgQ/edit
    design:
      css_class: dark
      background:
        color: black
        image:
          # Add your image background to assets/media/.
          filename: stacked-peaks.svg
          filters:
            brightness: 1.0
          size: cover
          position: center
          parallax: false

  - block: markdown
    content:
      title: '📚 Minat dan Penelitian Saya'
      subtitle: ''
      text: |-
        Saya berfokus pada pemanfaatan teknologi terbaru untuk memecahkan masalah yang kompleks. 
        Topik penelitian dan minat saya meliputi:
        
        - Pengembangan aplikasi berbasis AI untuk efisiensi data.
        - Blockchain untuk keamanan dan integritas data.
        - Pembuatan antarmuka pengguna (UI/UX) yang intuitif dan responsif.
        
        Jika Anda tertarik untuk berkolaborasi atau berdiskusi lebih jauh, silakan hubungi saya. 😊
    design:
      columns: '1'
  - block: collection
    id: panduan
    content:
      title: Panduan
      subtitle: ""
      text: ""
      # Page type to display. E.g. post, talk, publication...
      page_type: post
      # Choose how many pages you would like to display (0 = all pages)
      count: 5
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
      view: date-title-summary
      # Reduce spacing
      spacing:
        padding: [0, 0, 0, 0]
---
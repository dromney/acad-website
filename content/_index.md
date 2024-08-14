---
# Leave the homepage title empty to use the site title
title:
date: 2024-03-15
type: landing

sections:
  - block: about.avatar
    id: about
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
      # Override your bio text from `authors/admin/_index.md`?
      text:
    design:
      columns: '1'
      view: showcase
  - block: collection
    id: featured
    content:
      title: Current Work
      filters:
        folders:
          - publication
        featured_only: true
    design:
      columns: '2'
      view: card
  - block: tag_cloud
    content:
      title: Popular Topics
    design:
      columns: '2'
  - block: contact
    id: contact
    content:
      title: Contact
      subtitle:
      text: |-
      email: david.romney@byu.edu
      phone: +1 801 422 0364
      appointment_url: 'https://cal.com/romnoose/office-hours'
      address:
        street: 774 KMBL
        city: Provo
        region: UT
        postcode: "84602"
        country: United States
        country_code: US
      directions: Take elevator to floor 7 in KMBL tower
      office_hours:
        - "Office hours Fall 2024:"
        - "Tuesday 12-1pm"
        - "Thursday 10-11am"
        - "Friday 2-3pm"
    design:
      columns: '2'

---

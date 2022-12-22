---
# Leave the homepage title empty to use the site title
title:
date: 2022-12-21
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
      title: Featured Publications
      filters:
        folders:
          - publication
        featured_only: true
    design:
      columns: '2'
      view: card
  - block: contact
    id: contact
    content:
      title: Contact
      subtitle:
      text: |-
      email: david.romney@byu.edu
      phone: +1 801 422 0364
      # appointment_url: 'https://calendly.com' -->
      address:
        street: 734 KMBL
        city: Provo
        region: UT
        postcode: "84602"
        country: United States
        country_code: US
      directions: Take elevator to office 734 in KMBL tower
      office_hours:
        - "(Office hours for Winter 2023)"
        - 'Monday 11:00am--12:00pm'
        - 'Tuesday 3:00pm--4:00pm'
        - 'Wednesday 3:30pm--4:30pm'
        - 'Thursday 10:00am--11:00am'
    design:
      columns: '2'

---

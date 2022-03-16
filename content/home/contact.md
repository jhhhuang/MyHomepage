---
# An instance of the Contact widget.
widget: contact

# This file represents a page section.
headless: true

# Order that this section appears on the page.
weight: 130

title: Contact
subtitle:

content:
  # Automatically link email and phone or display as text?
  autolink: true
  
  # Email form provider
  form:
    provider: netlify
    formspree:
      id:
    netlify:
      # Enable CAPTCHA challenge to reduce spam?
      captcha: false

  # Contact details (edit or remove options as required)
  email: junhanhuang19@fudan.edu.cn
  phone: 153 592 311 31
  address:
    street: 220 Handan Rd
    city: Shanghai
    region: Yangpu District
    postcode: '200433'
    country: China
    country_code: CN
  coordinates:
    latitude: '31.29725466450779'
    longitude: '121.50358561090677'

design:
  columns: '2'
---

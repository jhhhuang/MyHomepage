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
  #form:
  #  provider: netlify
  #  formspree:
  #    id:
  #  netlify:
  #    # Enable CAPTCHA challenge to reduce spam?
  #    captcha: false

  # Contact details (edit or remove options as required)
  email: junhanhuang19@fudan.edu.cn
  phone: +8615359231131
  address:
    street: 220 Handan Rd
    city: Shanghai
    region: Yangpu District
    postcode: '200433'
    country: China
    country_code: CN
  coordinates:
    latitude: '31.297188'
    longitude: '121.503353'

design: 
  columns: '2'

<script src="lib/js/jquery.min.js"></script> <script src="lib/js/bootstrap.min.js"></script>

<script>
function myMap() {
    var uluru = {lat: your-latitude, lng: your-longitude};
    var map = new google.maps.Map(document.getElementById('map'), {
      zoom: 9,
      center: uluru
    });
    var marker = new google.maps.Marker({
      position: uluru,
      map: map
    });
}
</script>
  <script async defer src="https://maps.googleapis.com/maps/api/js?key=AIzaSyCVe9EfAXvTXXjZTqLg96iZklLOC_jyl3A&callback=initMap">
</script>
--- 

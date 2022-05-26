# smart-card-data-dashboard
Interactive dashboard for visualising Washington D.C. smart card transit data. Custom built for the agency using React.js

## Demo

### Limited vs. Local Stops

Limited stop services arrive less frequently than local service, but skip stops to provide faster travel time. Transit passengers must choose between taking the first bus that arrives or potentially waiting for a faster limited stop service. This page allows users to visualize the effects of adding or removing limited stop routes.

https://user-images.githubusercontent.com/59377951/170520104-c4267203-a0df-4d87-8679-3883895d1f53.mp4



### Transit Circuity

Two pages allow users to visualize transfer points throughout the network and the circuity of transit routes. The transfers page shows scheduled transfer times, actual times and the difference between the two, as well as the number of passengers transferring at each point. The circuity page shows the difference between the distance riders must travel on the bus and the straight-line or driving distance to their destinations.

https://user-images.githubusercontent.com/59377951/170519926-43152451-437a-4f3e-8cf4-f5ee329fb3d7.mp4

## Dashboard Architecture

This dashboard was custom-built for WMATA to display the data analysis conducted for its Bus Network Redesign, but some components could be adapted to produce similar dashboards for any transit agency or broader use cases.

- React v7
- React-leaflet
- React-vis
- React-router

The React-Leaflet package facilitates interactive mapping. A custom reusable map component underlies each page, with additional data layered on depending on the use case. Transit route shapes are provided through requests to the Transit.land REST API, and configured using React hooks to only make new requests when routes change. React-vis provides charting capabilities. For each page, data flows from a single parent component to child components rendering the maps and charts. State updates are managed in a single location in the parent component. 

React's state management allows for smoothly updating the chart and map components simultaneously based on user selections, and passing filtered data to chart components built using React-vis.

React-router provides browser routing without requiring additional Http requests.

Reusable components including the basemap configuration, modals, and navigation bars can be recycled for different use cases.

Although most data in this dashboard is static, if agencies required real-time updates they could expose their data through a REST API, which could be easily consumed by these react components and displayed on similar charts and maps.

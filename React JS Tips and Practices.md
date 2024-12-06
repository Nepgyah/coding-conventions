## Use inline functions sparingly
Each render will create a new instance of that function when ever the component is rendered. When the components are nested or get complicated, define the function once and use callbacks to improve efficiency. Use inline functions when you are sure renders of that component are few to a single time during its lifespan.

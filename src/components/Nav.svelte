
<div class="nav-div">
   <nav>
      <a href='/form'>Add New</a>
      <a href='/dashboard'>Worn</a>
      <a href='/closet'>Closet</a>
   </nav>
</div>


<style>
   .nav-div{
      width: 100%;
      background-color: var(--white);
   }

   nav{
      position: fixed;
      bottom: 0;
      text-align: center;
      display: flex;
      justify-content: space-around;
      width: 100%;
      background-color: var(--white);
      padding-top: 0.7rem;
   }

   a{
      color: var(--white);
      font-family: var(--heading);
      background-color: var(--teal);
      padding: 1rem;
   }

   /* Tablet styles */
   @media only screen and (min-width: 768px){

      a{
         font-size: 1.3rem;
         padding: 1.5rem;
      }

   }

   /* Desktop styles */
   @media only screen and (min-width: 1440px){

   a{
      font-size: 1.5rem;
      padding: 1.8rem;
   }

   }
</style>
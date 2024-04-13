This is a simple to do list created with Vanilla JavaScript, HTML and CSS. 

Things to consider: 
1. The project is not responsive
2. The JavaScript code is inside index.html since the project is small.

How it works: 

1. First we make the input field mandatory and return an error if it is empty.

       if (inputVal.value.trim() === "") {

        errors.innerHTML = "Field is mandatory!";

        setTimeout(function () {
          errors.innerHTML = "";

        }, 3000)

        return;


      }

2. If the field is not empty we proceed with dynamically adding the item.

else {


        container.insertAdjacentHTML('afterbegin', `
              <div class='items'>
              <input disabled class="output" type="text">
              <button class="editBTN">Edit</button>
              <button class="deleteBTN">Delete</button>
            </div>
            `);

        let inputList = document.querySelector('.output');
        inputList.style.background = "#00000029";

        inputList.value = inputVal.value;

        inputVal.value = "";

        deleteButton();

        editButton();

      }

The input field inside the item is disabled!              
<input disabled class="output" type="text">

Once the value is added to the new item, we clear the input field with the following code: 

inputVal.value = "";

Lastly we create the two functions for the Delete and for the Edit button:

1. Delete works by removing the closest parent element when clicking the delete button.

function deleteButton() {

let deleteBTN = document.querySelector('.deleteBTN');
let delEl = deleteBTN.closest('.items');

deleteBTN.addEventListener('click', function () {

delEl.remove();

})

}

2. Edit function works by enabling the closest input field with class "output" from "disabled" to "enabled".

   function editButton() {

      let editBtn = document.querySelector('.editBTN');

      let itms = editBtn.closest('.items');
      let foundResult = itms.querySelector('.output');

      editBtn.addEventListener('click', function () {

        if (foundResult.hasAttribute('disabled')) {



          foundResult.removeAttribute('disabled', '');
          foundResult.setAttribute('enabled', '');
          foundResult.style.background = "white";


        } else {

          foundResult.style.background = "#00000029";

          foundResult.setAttribute('disabled', '');
          foundResult.removeAttribute('enabled', '');

        }


      })


    }

Based on whether it is disabled or enabled we change the background color of the input.


I have the ready project uploaded here: https://lubodev.com/To-Do-List/index.html

:) 


      

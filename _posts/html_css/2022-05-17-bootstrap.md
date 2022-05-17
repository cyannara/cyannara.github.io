---
title: "bootstrap"
date: 2021-10-06
categories: html_css  
---

a. modal  
   1. modal.html  

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css" >
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/js/bootstrap.bundle.min.js" ></script>
<button type="button" class="btn btn-primary" id="btnModal" > Launch demo modal</button>
<div id="test"></div>
<script>
	btnModal.addEventListener("click", function(){
 		fetch("popup.jsp")
		.then(res => res.text())
		.then(res => {
			document.getElementById("test").innerHTML = res;
			const myModal = new bootstrap.Modal('#exampleModal');
			myModal.show()
		}) 
	});
</script>
```  

   2. popup.html  

```html
<!-- Modal -->
<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        ... ajax modal
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div>
  </div>
</div>
```   

b. grid  
   1. row, col
   2. test
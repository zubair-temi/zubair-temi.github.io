---
layout: default
title: تصانیف
permalink: /books/
---

<h1 style="text-align:center; padding-top: 30px; padding-bottom:30px;">تصانیف</h1>

<div class="row books">

    {% for book in site.data.books %}
        <div class="col-md-4 book">
            <div class="book-image">
                <a href="#bookModal" data-toggle="modal" 
                    data-book-desc="{{book.description | escape}}"
                    data-book-name="{{book.name | escape}}"
                    data-book-download="{{book.url}}"
                    data-book-pages="{{book.pages}}"
                    data-book-pub="{{book.publisher}}">
                    <img src="{{site.url}}/{{book.image}}" width="100" height="160" 
                    style="box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);">
                </a>
            </div>
            <div>
                <span><strong>{{ book.name }}</strong></span>
            </div>
        </div>
    {% endfor %}

</div>

<!-- Modal -->
<div class="modal fade" id="bookModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="bookTitle">Modal title</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body" >
        <div id="bookDesc"></div>
        <br>
        <div class="row">
            <div class="col-md-6" id="bookPages"></div>
            <div class="col-md-6" id="bookPublisher"></div>
        </div>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-primary" data-dismiss="modal">بند</button>
        <button type="button" class="btn btn-success" id="download" onclick="">
          <i class="far fa-file-pdf" style="color:#dc1e00;"></i>
          <span class="username">ڈاوٴنلوڈ</span>
        </button>
      </div>
    </div>
  </div>
</div>


<script>
//triggered when modal is about to be shown
$('#bookModal').on('show.bs.modal', function(e) {

    var desc = $(e.relatedTarget).data('book-desc');
    var name = $(e.relatedTarget).data('book-name');
    var pages = $(e.relatedTarget).data('book-pages');
    var publisher = $(e.relatedTarget).data('book-pub');
    var url = $(e.relatedTarget).data('book-download');
    var link = "window.location.href = '" + url + "';"
    //populate the textbox
    $(e.currentTarget).find('#bookTitle').html(name);
    $(e.currentTarget).find('#bookDesc').html(desc);
    $(e.currentTarget).find('#bookPages').html("صفحات: " + pages);
    $(e.currentTarget).find('#bookPublisher').html("ناشر: " + publisher);
    $(e.currentTarget).find('#download').attr('onclick', link);
});    
</script>
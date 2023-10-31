# Bookmarks clean up

　　Bookmarks clean up

　　document.querySelectorAll('body .duplicate.card .card-body ul li:first-child input ').forEach(item =\> {

　　item.checked = true

　　item.dispatchEvent(new Event('change'))

　　})

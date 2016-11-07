#Marking guide for "DIY Django Mini Blog"

The following guide outlines a marking guide for the MDN Learning Area Django Topic — [DIY Django Mini Blog](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/django_assessment_blog). Each subtask detailed in the assessment is listed below, along with an explanation of how many marks the task is worth, and the mark breakdown.

**Note:** There are numerous ways of implementing this application in Django. Any "sensible" mechanism that meets the requirements outlined in the assessment task would be deemed acceptable (that is why most of this testing is for compliance with the requirements rather than use of particular classes, etc.)

The overall mark awarded is out of 100. For reference, this project (TBD) contains a worked example that might receive full marks.

## Models

They need to:

* Create separate models for ``Blogs``, ``Comments``, and ``BlogAuthors`` (6 marks total).
  * 2 marks for having a model for blogs.
  * 2 marks for having a model for blog authors.
  * 2 marks for having a model for blog comments.
* Use correct date fields (4 marks total).
  * 2 marks for using a ``DateTimeField`` for Comments.
  * 2 marks for using either a ``DateField`` or a ``DateTimeField`` for Blogs.
* Define a ``__str__()`` method for all models (3 marks total).
* Define a ``get_absolute_url()`` method for Blogs and Blog Authors (2 marks).
* Use a ``ForeignKey`` field for the relationship between ``Users`` and ``BlogAuthors``, ``Blogs`` and ``BlogAuthors``, and between ``Blogs`` and ``Comments`` (3 marks total).

Hint: The relationships should look something like this:

  ![Django Blog Models](https://github.com/hamishwillee/django_diy_blog/blob/master/blog/static/images/diy_django_mini_blog_models.png)

## Admin site

They need to:
* Make blog, blog author, and blog comments visible and editable in the admin site (3 marks - 1 for each).
* Make blog detail listings display comments underneath (2 marks).
* Make only those comments that exist display (i.e. no placeholder for creating new comments) - 2 marks.


## Pages

They need to create pages for:

* Listing all blogs (5 marks total).
  * 1 marks for listing all blogs.
  * 1 mark for paginating it.
  * 1 mark for paginating in lots of 5.
  * 2 marks for ordering newest to oldest.
* Showing detail for a blog (16 marks total).
  * 0.5 marks for listing each of blog: title, description, date, author.
  * 2 marks if author is a link to author detail.
  * 2 marks for listing all comments.
  * 2 marks for listing comments in order: oldest to newest.
  * 2 marks for having a link to 'add new comments'.
  * 2 marks if the link displays only if the user is logged in.
  * 2 marks if the link does not display when the user is logged out (or links to the login page).
* Adding comments (6 marks total).
  * 2 marks if form only contains description (not author/date post).
  * 2 marks if it can only be used by logged in users (redirects to login if they attempt to access it via URL when not logged in).
  * 2 marks if the page contains the name of the blog that the comment is being added to.
* Listing all authors (3 marks total).
  * 3 marks for listing all authors.
* Showing detail for an author (5 marks total).
  * 1 marks for showing author name.
  * 1 marks for showing bio.
  * 1 marks for listing all their blogs.
  * 1 mark if the blog list is in order: newest to oldest.
  * 1 mark if blog titles are links to blogs.
* Logging in/out (5 marks total).
  * 3 marks if there are links to log in/out pages on all pages.
  * 2 marks if the links are appropriate (i.e. log out if the user is logged in, and visa versa).
* Index page (4 marks total).
  * 2 marks if it is displayed from the URL **/blog/**.
  * 2 marks if it is displayed from the root URL (**/**).

## Tests

They need to write basic tests to verify that:

* All model fields have the correct label and length (10 marks total).
  * 0.5 marks for each function to check field verbose name and length for ``BlogAuthor`` (user, bio), ``Blog`` (name, author, description, post_date), and ``BlogComment`` (description, author, post_date, blog).
* All models have the expected object name (9 marks total).
  * 2 marks for each function to check that the string value of ``BlogAuthor`` (2) and ``Blog`` (2) are as expected.
  * 5 marks if the ``BlogComment`` function checks that the ``Blog`` comment is the description truncated to 75 characters.
* Models return the expected URL from ``get_absolute_url()`` (4 marks total).
  * 2 marks each for test functions in Blog and Comment.
* the list of all blogs is returned at the correct URLs (8 marks total).
  * 2 marks for a test that list page available at */blog/blogs*.
  * 2 marks for a test that list page available at named URL 'blogs" via the ``reverse()`` function.
  * 2 marks for a test that shows the view used the expected template (e.g. the default).
  * 2 marks for a test that verifies that the view paginates blogs in sets of 5 (just test the first page).

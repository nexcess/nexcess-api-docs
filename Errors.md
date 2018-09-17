# Errors

The most common errors occur with the POST verb. They deal with a lack of required parameters or invalid values for parameters. In these cases a 4** series error will be returned along with an error message identifying the problem.

Occasionally, a 4** error will be returned if a GET is sent without required parameters or valid values.

In rare cases the system will return a 5** series error. These are errors are problems with the underlying system. The fact that you received it means that we have received a message about it as well.

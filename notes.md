# Responsive Layouts Simplified

- Websites are responsive before we write any CSS
- When our layouts run into issues, we're at fault.
- Usually (though not always), a desktop-first approach is the culprit.
- Writing mobile-first CSS tends to be the easier way to approach it as well, even if you only have a desktop layout to base things off of.

- Following are the two approaches to built same layout.

```
# Desktop-first approach

.row {
    display:flex;
    justify-content:space-between;
}

.main-content {
    width:62%;
}

.sidebar{
    width:32%;
}


@media (max-width:700px){
    .row {
        display:block;
    }

    .main-content,
    .sidebar {
        width:100%
    }
}

```

```
# Mobile-first Approach

@media (min-width:700px){
    .row {
        display:flex;
        justify-contnt:space-between;
    }

    .main-content {
        width:62%;
    }

    .sidebar {
        width:32%
    }
}
```

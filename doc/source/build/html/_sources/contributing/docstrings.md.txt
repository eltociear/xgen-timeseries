(docstrings)=
# Docstring style

Docstrings should follow the
[numpy docstring guide](https://numpydoc.readthedocs.io/en/latest/format.html). Read more about it {ref}`docstring_formatting`.
In XGenTS docs, docstrings consit of five main sections, i.e.,
1. Short summary
2. Parameters
3. Returns
4. See Also
5. Examples
Extended summary is strongly encouraged and references is required when relevant in order to cite the papers proposing or explaining the algorithms that are implemented. All other sections can also be used when convenient.

## References
While adding description of parameters, examples, etc, it is important to add references to external libraries and XGenTS.
Docstrings follow the same guide for adding references as the other docs.
For adding references to external libraries functions and objects, see {ref}`reference_external_libs`. For referencing XGenTS objects, follow {ref}`reference_XGenTS_objects`.

## See Also
In XGenTS docs, we have a lot of interconnected functions both within the library and with external libraries and it can take a lot of time to search for the related functions. It is cruical to add the See Also section to save users time.
For adding the _See Also_ docstring section, you just need to add the function name. Sphinx will
automatically add links to other XGenTS objects and functions listed in the _See Also_
section.

For example, let's add {func}`~XGenTS.hdi` and {func}`~XGenTS.plot_ppc` in the _See Also_ section.

```
    See Also
    --------
    hdi : Calculate highest density interval (HDI) of array for given probability.
    plot_ppc : plot for posterior/prior predictive checks.
```

## Kwargs parameters
All the kwargs parameters in {ref}`plots <plot_api>` modules are passed to the matplotlib or bokeh functions. While writing their description, the functions to which they are being passed must be mentioned. In order to check or add those functions, the process is the same for all the kwargs arguments. Let's read the step-by-step guide for `backend_kwargs` as an example, [here](https://github.com/XGenTS-devs/XGenTS/wiki/XGenTS-Hacktoberfest-2021).

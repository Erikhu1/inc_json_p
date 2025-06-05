load("@score_docs_as_code//:docs.bzl", "docs")

# Creates all documentation targets:
# - `docs:incremental` for building docs incrementally at runtime
# - `docs:live_preview` for live preview in the browser without an IDE
# - `docs:ide_support` for creating python virtualenv for IDE support
# - `docs:docs` for building documentation at build-time

docs(
    #   conf_dir = "docs",
    docs_targets = [
        {
            "suffix": "",  # local without external needs
        },
    ],
    #   source_dir = "docs",
    source_files_to_scan_for_needs_links = [],
)
genrule(
    name = "github_pages",
    srcs = [],  # add any source files needed for the docs, or leave empty if not needed
    outs = ["github_pages_dummy.txt"],  # dummy output file
    cmd = "echo 'This is a placeholder for the github_pages target.' > $@",
)

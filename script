import os
import shutil
import markdown
from jinja2 import Environment, FileSystemLoader, select_autoescape

# Input and output directories
input_dir = "input"
output_dir = "output"

# Initialize Jinja2 environment
env = Environment(
    loader=FileSystemLoader("templates"),
    autoescape=select_autoescape(["html", "xml"])
)

# Load the templates
index_template = env.get_template("index.html")
article_template = env.get_template("article.html")
about_template = env.get_template("about.html")
contact_template = env.get_template("contact.html")
error_template = env.get_template("error.html")

# Generate the index page
with open(os.path.join(input_dir, "index.md"), "r") as f:
    index_md = f.read()
    index_html = index_template.render(content=markdown.markdown(index_md))
    with open(os.path.join(output_dir, "index.html"), "w") as f:
        f.write(index_html)

# Generate the article pages
for filename in os.listdir(os.path.join(input_dir, "articles")):
    if filename.endswith(".md"):
        with open(os.path.join(input_dir, "articles", filename), "r") as f:
            article_md = f.read()
            article_html = article_template.render(content=markdown.markdown(article_md))
            with open(os.path.join(output_dir, "articles", os.path.splitext(filename)[0] + ".html"), "w") as f:
                f.write(article_html)

# Generate the about page
for filename in os.listdir(os.path.join(input_dir, "about")):
    if filename.endswith(".md"):
        with open(os.path.join(input_dir, "about"), "r") as f:
            about_md = f.read()
            about_html = about_template.render(content=markdown.markdown(about_md))
            with open(os.path.join(output_dir, "about.html"), "w") as f:
                f.write(about_html)

# Generate the contact page
with open(os.path.join(input_dir, "contact.md"), "r") as f:
    contact_md = f.read()
    contact_html = contact_template.render(content=markdown.markdown(contact_md))
    with open(os.path.join(output_dir, "contact.html"), "w") as f:
        f.write(contact_html)

# Generate the error pages
for error_code in [404, 500]:
    with open(os.path.join(input_dir, f"{error_code}.md"), "r") as f:
        error_md = f.read()
        error_html = error_template.render(code=error_code, content=markdown.markdown(error_md))
        with open(os.path.join(output_dir, f"{error_code}.html"), "w") as f:
            f.write(error_html)

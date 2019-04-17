# Hydejack Starter Kit

A quicker, cleaner way to get started blogging with [Hydejack](https://hydejack.com/).

## Quick Start
### Running locally
1. Clone repository (git users), or [download] and unzip.
2. Open terminal, `cd` into root directory (where `_config.yml` is located)
3. `bundle install` [^1]
4. `bundle exec jekyll serve`
5. Open <http://localhost:4000/hy-starter-kit/>

### GitHub Pages
1. Fork this repository.
2. Go to **Settings**, rename repository to `<your github username>.github.io` (without the `<` `>`)
3. Edit `_config.yml` (you can do this directly on GitHub)
    1. Change `url` to `https://<your github username>.github.io` (without the `<` `>`)
    2. Change `baseurl` to `''` (empty string)
    3. **Commit changes**.
4. Go to **Settings** again, look for **GitHub Pages**, set **Source** to **master branch**.
5. Click **Save** and wait for GitHub to set up your new blag.

## TODO
**Update the following posts:**
* ~~2017-08-04-hello-world.md~~
* ~~2017-11-15-sample-sending-email.md~~
* ~~2017-11-15-tips-of-mysql.md~~
* ~~2017-11-16-sample-jdbc-good-practice.md~~
* ~~2017-11-17-will-neo-be-the-next-big-thing.md~~
* ~~2017-12-09-95-865-unstructured-data-analytics.md~~
* ~~2018-01-14-database-management-review-framework.md~~
* ~~2018-07-25-example-jdbc-better-practicestream-sql-request.md~~
* ~~2018-11-05-17-682-java-ee-web-application.md~~
* ~~2019-03-02-some-notes-on-spark-data-engineering-on-the-cloud.md~~

[^1]: Requires Bundler. Install with `gem install bundler`.

[download]: https://github.com/qwtel/hy-starter-kit/archive/master.zip

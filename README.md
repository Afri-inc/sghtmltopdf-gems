# sghtmltopdf-gems

Prebuilt [sghtmltopdf](https://github.com/waka/sghtmltopdf) gems for SENRI, built from upstream commits that have not been released to rubygems.org yet. GitHub Pages serves this repository as a static gem source.

```ruby
# Gemfile
source 'https://afri-inc.github.io/sghtmltopdf-gems' do
  gem 'sghtmltopdf', '0.5.1.g257bf07'
end
```

## Versions

The version is the upstream gem version plus `g` and the short hash of the upstream commit the gem was compiled from.

| Version | Upstream commit | Build branch (fork) | Build run | Platforms | Ruby |
|---|---|---|---|---|---|
| `0.5.1.g257bf07` | [`257bf0752e5e805cc5bd4d6d53ecc231dfcdc91d`](https://github.com/waka/sghtmltopdf/commit/257bf0752e5e805cc5bd4d6d53ecc231dfcdc91d) | [`dai199/sghtmltopdf@build/gem-257bf07`](https://github.com/dai199/sghtmltopdf/tree/build/gem-257bf07) | [38505717771](https://github.com/dai199/sghtmltopdf/actions/runs/38505717771) | `aarch64-linux`, `x86_64-linux`, `arm64-darwin` | 3.4, 4.0 |

The build branch is the upstream commit plus one commit that sets the version and narrows `.github/workflows/gem.yml` to the platforms and Ruby versions above. The gems are built by that workflow (`workflow_dispatch`, `dry_run: true`), so nothing is published to rubygems.org.

## Adding a version

1. Branch from the upstream commit on the fork, set `bindings/ruby/lib/sghtmltopdf/version.rb` to `<upstream version>.g<short hash>`, and apply the same workflow change as the previous build branch.
2. Run the `gem` workflow on that branch and download the three `gem-*` artifacts.
3. Copy the `.gem` files into `gems/`, run `gem generate_index --directory .`, add a row to the table above, and push to `main`.


[dataframes like pandas](https://github.com/ankane/polars-ruby) --> [interactive charts for ruby](https://github.com/ankane/vega-ruby#ot)

echo "gem: --user-install" > /etc/gemrc
echo "gem: --user-install" > $HOME/.gemrc

gem install bundle

BUNDLE_PATH="/home/b08x/.local/share/gem/ruby/3.0.0" bundle install
yard gems

Note that we won't be able to show the key to you again. New API key: ``
85

Consider installing pyenv with Homebrew on macOS

brew update
brew install pyenv
OR Clone the repository to get the latest version of pyenv

 git clone https://github.com/pyenv/pyenv.git ~/.pyenv
Define your environment variables

echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
source ~/.bash_profile
Restart your shell so the path changes take effect

exec "$SHELL"
Verify the installation and check the available python versions

pyenv install --list
Install the required python version

pyenv install 3.7
Set it as your global version after installation

pyenv global 3.7
Verify your current python version the system is using

python3 --version

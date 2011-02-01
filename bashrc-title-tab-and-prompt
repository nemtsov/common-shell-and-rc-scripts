#===========================================

# Retrieves the name of the current directory
# with it's parent directory in the following format:
# "<PARENT_DIR>/<CURRENT_DIR>". If the result
# of this is the user's $HOME, tilde (~) will be
# returned. Tilde will also be substituted for
# the <PARENT_DIR> when it is the user's $HOME dir.
get_pwdbase() {
  if [ "$PWD" == $HOME ]; then
    echo "~" 
    exit 0
  fi

  local parent=$(basename "$(dirname "$PWD")")
  if [ "$(dirname "$PWD")" == $HOME ]; then
    parent="~"
  fi

  echo $parent/$(basename "$PWD")
}

# Updates the terminal tab title with the parent and currrent working dir;
# and sets-up the bash prompt with 'username@host:working-dir$ '
set_title_tab_and_prompt() {
  if [ $TERM = xterm ]; then
    local title="\[\033]2;\w\007\]"
    local tab="\[\033]1;$(get_pwdbase)\007\]"
    PS1="${title}${tab}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]$(get_pwdbase)\[\033[00m\]\$ "
  fi
}

PROMPT_COMMAND='set_title_tab_and_prompt'

#===========================================

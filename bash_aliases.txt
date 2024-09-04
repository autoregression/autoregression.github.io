function gp {
  local branch=${1:-$(git rev-parse --abbrev-ref HEAD)}
  git pull origin $branch
}

function gpp {
  local message=${1:-"update"}
  git pull
  git add .
  git commit -m "$message"
  git push
}

function gc {
  local message=${1:-"update"}
  git commit -m "$message"
}

function t {
  local devices=${1:-0}
  local path=$2
  CUDA_VISIBLE_DEVICES=$devices python train.py $path
}

function tt {
  local devices=${1:-0}
  local path=$2
  CUDA_VISIBLE_DEVICES=$devices WANDB_MODE=disabled COMPILE=false python train.py $path
}

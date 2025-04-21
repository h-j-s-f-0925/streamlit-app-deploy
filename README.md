# streamlit-app-deploy
streamlit の学習


# ディレクトリ構成
```bash
streamlit-app-deploy/           ← プロジェクトルート
    ├── pyproject.toml
    ├── main.py
    ├── app.py
    ├── requirements.txt
    ├── README.md
    ├── .gitignore

```


# 作業手順
- GitHub で、streamlit-app-deploy リポジトリを作成

```bash
# streamlit-app-deploy フォルダを作成

# git clone git@github.com:h-j-s-f-0925/streamlit-app-deploy.git

# cd streamlit-app-deploy

poetry init --no-interaction --name streamlit-app-deploy --description "streamlitの練習用" --author "hoge" --license "MIT"

# .venv フォルダがプロジェクトフォルダ内に生成されるように設定
poetry config virtualenvs.in-project true --local  
poetry config --list

poetry add streamlit==1.41.1

poetry env info

# 仮想環境を表示
Invoke-Expression (poetry env activate) 

poetry show

# 仮想環境に入っているので、そのまま、pyton src/main.py でスクリプトの実行
python src/env_practice/main.py

# 仮想環境から出る
deactivate

# which python で、仮想環境のパスが消えていることを確認 
which python


```


```bash
# 依存状況を共有
# pip freeze > requirements.txt は、Poetry では不要
→ pyproject.toml と poetry.lock をGitにコミット


```

# デプロイ
- Streamlit では、poetry install --no-root を指定できない
- requeirements.txt を作成して、デプロイする
```bash
poetry self add poetry-plugin-export

poetry export -f requirements.txt --without-hashes -o requirements.txt
```
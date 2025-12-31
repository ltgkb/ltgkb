## Hi there 👋

<!--
**ltgkb/ltgkb** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
# Hi there! 👋
 
我是 [ltgkb]，一名开发者。

---

⏳ **自动更新时间**
注意： `.*/\nLast Updated: $DATE (UTC)\n/z" README.md || true # 注意：上面的 sed 写法比较简略，为了通用性，我们用下面更稳妥的脚本方式：

  - name: Run Update Script
    run: |
      # 获取当前日期
      NOW=$(date "+%Y-%m-%d %H:%M:%S")
      
      # 定义要写入的内容
      CONTENT="Last Updated: $NOW (UTC)"
      
      # 使用 perl 替换两行注释中间的内容 (比 sed 更跨平台稳定)
      perl -i -0777 -pe "s/()(.*?)()/\$1\n$CONTENT\n\$3/s" README.md

  - name: Commit and Push
    run: |
      git config --global user.name "GitHub Action"
      git config --global user.email "action@github.com"
      
      # 检查是否有文件变动
      if [[ -n $(git status -s) ]]; then
        git add README.md
        git commit -m "Auto update README time [skip ci]"
        git push
        echo "✅ README updated successfully."
      else
        echo "⚠️ No changes to commit."
      fi

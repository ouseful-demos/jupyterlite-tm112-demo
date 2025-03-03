# Quarto pipeline


 quarto add r-wasm/quarto-live

 
mkdir -p quarto_docs

for file in *.ipynb; do
    quarto convert "$file" -o "quarto_docs/${file%.ipynb}.qmd"
done


Linux:

for file in quarto_docs/*.qmd; do
    #sed '1,/^---/ { /^---/ {n; s/.*/format: live-html/; } }' "$file"
    sed 's/{python}/{pyodide}/g' "$file"
done


Mac:

for file in quarto_docs/*.qmd; do
    #sed -i '' '1,/^---/ { /^---/ {n; s/.*/format: live-html/; } }' "$file"
    sed -i '' 's/{python}/{pyodide}/g' "$file"
done



## Quarto

quarto add --no-prompt r-wasm/quarto-live

quarto render src/FILE.Rmd --output-dir ../quarto_dist
quarto render quarto_docs/ --no-execute --output-dir ../quarto_dist

Site rendered to quarto_docs/_site/


python3 -m http.server 8128 -d ./quarto_dist
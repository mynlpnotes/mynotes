# The Recipes Dataset

*   20000 recipes with metadata such as nutritional information and ingredient list

    ```bash
    bash scripts/download_kaggle_data.sh hugodarwood epirecipes
    ```
* Loading the data:
*   <mark style="color:purple;background-color:purple;">**It has list of dictionary which has title, directions etc**</mark>

    ```python
    with open('/app/data/epirecipes/full_format_recipes.json') as json_data:
        recipe_data = json.load(json_data)

    filtered_data = [
        'Recipe for ' + x['title']+ ' | ' + ' '.join(x['directions'])
        for x in recipe_data
        if 'title' in x
        and x['title'] is not None
        and 'directions' in x
        and x['directions'] is not None
    ]
    ```
*

    <figure><img src="../../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

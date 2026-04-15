In this repository, Fungal strains with different genotypes are tested under two scenarios( 90% dominance of double resistant strain in total infected compartment and disease dynamics ) under 3 scenarios (zero fungicide use, partial resistance and full resistance). 


For conversion of table generated in python into LaTex format following code was used. ( example for generating "Baseline scenario" table)
step = max(1, len(df_time) // 25) 
df_to_export = df_time.iloc[::step].copy()
df_to_export.columns = ["Time", "$H$", "$I_{ab}$", "$I_{Ab}$", "$I_{aB}$", "$I_{AB}$"]

latex_table = df_to_export.style.hide(axis="index").format(
    subset=["Time"], formatter="{:.1f}"
).format(
    subset=["$H$", "$I_{ab}$", "$I_{Ab}$", "$I_{aB}$", "$I_{AB}$"], 
    formatter="{:.3e}"
).to_latex(
    hrules=True, # This replaces 'booktabs=True'
    caption="Baseline scenario (No fungicide use)",
    label="tab:baseline_no_fungicide",
    position="htbp",
    column_format="lccccc"
)
print(latex_table)

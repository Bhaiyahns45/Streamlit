## Streamlit


    # ---- HIDE STREAMLIT STYLE ----
    hide_st_style = """
                <style>
                #MainMenu {visibility: hidden;}
                footer {visibility: hidden;}
                header {visibility: hidden;}
                </style>
                """
    st.markdown(hide_st_style, unsafe_allow_html=True)

---


    # Live footer
    footer_html = """
    <div style="position: fixed; bottom: 0; width: 100%; background-color: #f0f0f0; padding: 0px; text-align: center;">
        Bhaiya & Company © 2023
    </div>
    """
    st.write(footer_html, unsafe_allow_html=True)

---

    # Style for the "Run" button
    button_style = "background-color: green; color: white; font-weight: bold; padding: 8px 20px; border: none; border-radius: 5px;"
    
    # Solve button
    if st.button("Run Algo", key="run_button"):
        with st.spinner("Running the algorithm..."):
            optimal_x, optimal_y = solve_linear_programming()
            time.sleep(1)  # Simulate algorithm execution time
        st.success("Optimization complete!")
    
        if optimal_x is not None and optimal_y is not None:
            st.write(f"x = {optimal_x}")
            st.write(f"y = {optimal_y}")
        else:
            st.error("Optimization did not converge to an optimal solution.")
    
    # Apply button style using HTML and Markdown
    st.write(f"<style>div.stButton > button:first-child {{ {button_style} }}</style>", unsafe_allow_html=True)

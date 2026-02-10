from manim import *

class DerivativeIntro(Scene):
    def construct(self):
        # Оси
        axes = Axes(
            x_range=[-0.5, 4, 1],
            y_range=[-0.5, 8, 2],
            x_length=8,
            y_length=6,
            axis_config={
                "include_ticks": False,
                "include_numbers": False,
            }
        )

        # Подписи осей
        x_label = MathTex("x").next_to(axes.x_axis.get_end(), RIGHT)
        y_label = MathTex("y").next_to(axes.y_axis.get_end(), UP)

        # Функция (экспоненциальный вид, как на изображении)
        graph = axes.plot(
            lambda x: 0.4 * np.exp(0.9 * x),
            x_range=[-0.5, 3.2],
            color=ORANGE,
            stroke_width=6
        )

        # Формула производной
        formula = MathTex(
            r"f'(x)=\lim_{\Delta x\to 0}\frac{\Delta y}{\Delta x}"
        )

        frame = SurroundingRectangle(
            formula,
            color=GREEN,
            buff=0.4,
            stroke_width=4
        )

        formula_group = VGroup(formula, frame)
        formula_group.to_corner(RIGHT)

        # Анимация
        self.play(Create(axes), run_time=2)
        self.play(Write(x_label), Write(y_label))
        self.play(Create(graph), run_time=3)
        self.wait(0.5)
        self.play(Write(formula))
        self.play(Create(frame))
        self.wait(2)



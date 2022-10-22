# calculator_1
import sys
from PyQt6.QtCore import Qt
from PyQt6.QtWidgets import QApplication, QLabel, QPushButton, QVBoxLayout, QHBoxLayout, QWidget, QSpacerItem, QSizePolicy
from PyQt6.QtGui import QFont


class MyWindow(QWidget):

    def __init__(self):
        super(MyWindow, self).__init__()
        self.setGeometry(100, 100, 465, 480)
        self.setFixedSize(465, 480)
        self.setWindowTitle("calculator")
        self.setStyleSheet('background-color: rgb(120, 51, 30)')
        self.font1 = QFont()
        self.font1.setFamily('Agency FB')
        self.font1.setPointSize(30)
        self.font2 = QFont()
        self.font2.setFamily('Agency FB')
        self.font2.setPointSize(22)
        self.display_text = ""
        self.answered = False
        self.vBox = QVBoxLayout()
        self.setLayout(self.vBox)
        self.hBox_0 = QHBoxLayout()
        self.vBox.addLayout(self.hBox_0)
        spacerItem = QSpacerItem(40, 20, QSizePolicy.Policy.Expanding,
                                 QSizePolicy.Policy.Minimum)
        self.vBox.addItem(spacerItem)

        spacerItem = QSpacerItem(40, 20, QSizePolicy.Policy.Expanding,
                                 QSizePolicy.Policy.Minimum)
        self.vBox.addItem(spacerItem)

        self.hBox_1 = QHBoxLayout()
        self.vBox.addLayout(self.hBox_1)
        self.hBox_2 = QHBoxLayout()
        self.vBox.addLayout(self.hBox_2)
        self.hBox_3 = QHBoxLayout()
        self.vBox.addLayout(self.hBox_3)
        self.hBox_4 = QHBoxLayout()
        self.vBox.addLayout(self.hBox_4)

        self.vBox.setSpacing(15)

        self.result()
        self.add_buttons()


    def result(self):
        self.label = QLabel('0')
        self.label.setStyleSheet('background-color: white')
        self.hBox_0.addWidget(self.label)
        self.label.setAlignment(Qt.AlignmentFlag.AlignRight)
        self.label.setMargin(10)
        self.label.setFont(self.font1)


    def add_buttons(self):
        self.seven = QPushButton('7')
        self.hBox_1.addWidget(self.seven)
        self.seven.setStyleSheet('background-color: white')
        self.seven.setFont(self.font1)
        self.seven.clicked.connect(self.seven_clicked)


        self.eight = QPushButton('8')
        self.hBox_1.addWidget(self.eight)
        self.eight.setStyleSheet('background-color: white')
        self.eight.setFont(self.font1)
        self.eight.clicked.connect(self.eight_clicked)

        self.nine = QPushButton('9')
        self.hBox_1.addWidget(self.nine)
        self.nine.setStyleSheet('background-color: white')
        self.nine.setFont(self.font1)
        self.nine.clicked.connect(self.nine_clicked)

        self.plus = QPushButton('+')
        self.hBox_1.addWidget(self.plus)
        self.plus.setStyleSheet('background-color: white')
        self.plus.setFont(self.font1)
        self.plus.clicked.connect(self.plus_clicked)

        self.minus = QPushButton('-')
        self.hBox_1.addWidget(self.minus)
        self.minus.setStyleSheet('background-color: white')
        self.minus.setFont(self.font1)
        self.minus.clicked.connect(self.minus_clicked)


        self.four = QPushButton('4')
        self.hBox_2.addWidget(self.four)
        self.four.setStyleSheet('background-color: white')
        self.four.setFont(self.font1)
        self.four.clicked.connect(self.four_clicked)

        self.five = QPushButton('5')
        self.hBox_2.addWidget(self.five)
        self.five.setStyleSheet('background-color: white')
        self.five.setFont(self.font1)
        self.five.clicked.connect(self.five_clicked)

        self.six = QPushButton('6')
        self.hBox_2.addWidget(self.six)
        self.six.setStyleSheet('background-color: white')
        self.six.setFont(self.font1)
        self.six.clicked.connect(self.six_clicked)

        self.multiply = QPushButton('x')
        self.hBox_2.addWidget(self.multiply)
        self.multiply.setStyleSheet('background-color: white')
        self.multiply.setFont(self.font1)
        self.multiply.clicked.connect(self.multiply_clicked)

        self.divide = QPushButton('/')
        self.hBox_2.addWidget(self.divide)
        self.divide.setStyleSheet('background-color: white')
        self.divide.setFont(self.font2)
        self.divide.clicked.connect(self.divide_clicked)

        self.one = QPushButton('1')
        self.hBox_3.addWidget(self.one)
        self.one.setStyleSheet('background-color: white')
        self.one.setFont(self.font1)
        self.one.clicked.connect(self.one_clicked)

        self.two = QPushButton('2')
        self.hBox_3.addWidget(self.two)
        self.two.setStyleSheet('background-color: white')
        self.two.setFont(self.font1)
        self.two.clicked.connect(self.two_clicked)

        self.three = QPushButton('3')
        self.hBox_3.addWidget(self.three)
        self.three.setStyleSheet('background-color: white')
        self.three.setFont(self.font1)
        self.three.clicked.connect(self.three_clicked)

        self.parentheses_left = QPushButton('(')
        self.hBox_3.addWidget(self.parentheses_left)
        self.parentheses_left.setStyleSheet('background-color: white')
        self.parentheses_left.setFont(self.font1)
        self.parentheses_left.clicked.connect(self.parentheses_left_clicked)

        self.parentheses_right = QPushButton(')')
        self.hBox_3.addWidget(self.parentheses_right)
        self.parentheses_right.setStyleSheet('background-color: white')
        self.parentheses_right.setFont(self.font1)
        self.parentheses_right.clicked.connect(self.parentheses_right_clicked)

        self.zero = QPushButton('0')
        self.hBox_4.addWidget(self.zero)
        self.zero.setStyleSheet('background-color: white')
        self.zero.setFont(self.font1)
        self.zero.clicked.connect(self.zero_clicked)

        self.back = QPushButton('Back')
        self.hBox_4.addWidget(self.back)
        self.back.setStyleSheet('background-color: white')
        self.back.setFont(self.font2)
        self.back.clicked.connect(self.back_clicked)

        self.clear = QPushButton('Clear')
        self.hBox_4.addWidget(self.clear)
        self.clear.setStyleSheet('background-color: white')
        self.clear.setFont(self.font2)
        self.clear.clicked.connect(self.clear_clicked)

        self.decimal = QPushButton('.')
        self.hBox_4.addWidget(self.decimal)
        self.decimal.setStyleSheet('background-color: white')
        self.decimal.setFont(self.font1)
        self.decimal.clicked.connect(self.decimal_clicked)

        self.equal = QPushButton('=')
        self.hBox_4.addWidget(self.equal)
        self.equal.setStyleSheet('background-color: white')
        self.equal.setFont(self.font1)
        self.equal.clicked.connect(self.equal_clicked)


    def reset(self):
        if self.answered:
            self.label.setFont(self.font1)
            self.display_text = ""
            self.answered = False
            self.label.setText('0')

    def operation(self, operator):
        if self.answered and (int(self.display_text[-1]) in (range(0, 10))):
            self.display_text += operator
            self.label.setText(self.display_text)
            self.answered = False

        else:
            self.reset()
            try:
                if self.display_text[-1] not in ["/", '+', "x", "-", "*", '(']:
                    self.display_text += operator
                    self.label.setText(self.display_text)
                else:
                    pass
            except:
                pass


    def clear_clicked(self):
        self.label.setFont(self.font1)
        self.answered = False
        self.display_text = ""
        self.label.setText('0')


    def back_clicked(self):
        if self.display_text == "":
            pass
        elif self.answered:
            pass
        elif len(self.display_text) == 1:
            self.display_text = ""
            self.label.setText('0')
        else:
            self.display_text = self.display_text.replace(self.display_text[-1], "")
            self.label.setText(self.display_text)


    def zero_clicked(self):
        self.reset()
        if len(self.display_text) == 0:
            pass
        else:
            self.display_text += '0'
            self.label.setText(self.display_text)


    def one_clicked(self):
        self.reset()
        self.display_text += '1'
        self.label.setText(self.display_text)


    def two_clicked(self):
        self.reset()
        self.display_text += '2'
        self.label.setText(self.display_text)


    def three_clicked(self):
        self.reset()
        self.display_text += '3'
        self.label.setText(self.display_text)


    def four_clicked(self):
        self.reset()
        self.display_text += '4'
        self.label.setText(self.display_text)


    def five_clicked(self):
        self.reset()
        self.display_text += '5'
        self.label.setText(self.display_text)


    def six_clicked(self):
        self.reset()
        self.display_text += '6'
        self.label.setText(self.display_text)


    def seven_clicked(self):
        self.reset()
        self.display_text += '7'
        self.label.setText(self.display_text)


    def eight_clicked(self):
        self.reset()
        self.display_text += '8'
        self.label.setText(self.display_text)


    def nine_clicked(self):
        self.reset()
        self.display_text += '9'
        self.label.setText(self.display_text)


    def plus_clicked(self):
        self.operation('+')


    def minus_clicked(self):
        self.operation('-')


    def multiply_clicked(self):
        self.operation('x')


    def divide_clicked(self):
        self.operation('/')


    def parentheses_left_clicked(self):
        if self.answered:
            self.display_text += "x("
            self.label.setText(self.display_text)
            self.answered = False
        else:
            self.reset()
            if len(self.display_text) == 0:
                self.display_text += '('
            else:
                if self.display_text[-1] in ["/", '+', "x", "-", "*", '('] :
                    self.display_text += '('
                elif int(self.display_text[-1]) in (range(0, 10)):
                    self.display_text += "x("
                else:
                    self.display_text += '('
            self.label.setText(self.display_text)


    def parentheses_right_clicked(self):
        if self.answered:
            pass
        else:
            self.reset()
            if self.display_text == "":
                pass
            elif self.display_text[-1] == '()' or self.display_text[-1] == '.':
                pass
            else:
                self.display_text += ')'
                self.label.setText(self.display_text)


    def equal_clicked(self):
        if self.display_text[-1] in ['(', "."]:
            pass
        else:
            try:
                self.answered = True
                if 'x' in self.display_text:
                    self.display_text = self.display_text.replace('x', '*')
                self.display_text = str(eval(self.display_text))
                if len(self.display_text) > 20:
                    self.label.setFont(self.font2)
                    self.label.setText('Result too large!')
                else:
                    self.label.setText(self.display_text)
            except:
                self.answered = True
                self.display_text = ""
                self.label.setText('Invalid Entry')

    def decimal_clicked(self):
        if self.display_text[-1] in ["/", '+', "x", "-", "*", '(', ""]:
            self.display_text += "0."
            self.label.setText(self.display_text)
        elif self.display_text[-1] == '.':
            pass
        else:
            self.display_text += "."
            self.label.setText(self.display_text)



app = QApplication(sys.argv)
window = MyWindow()
window.show()
sys.exit(app.exec())


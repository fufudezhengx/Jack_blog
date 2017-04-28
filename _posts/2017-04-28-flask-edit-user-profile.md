---
layout: default
title: flask-用户资料编辑页面的疑问
---

## {{ page.title }}

	@main.route('/edit_profile',methods=['GET','POST'])
	@login_required
	def edit_profile():
    form = EditProfileForm()
    if form.validate_on_submit():
        current_user.name = form.name.data
        current_user.location = form.location.data
        current_user.about_me = form.about_me.data
        db.session.add(current_user)
        db.session.commit()
        flash('Your profile have been updated')
        return redirect(url_for('main.user_profile',username=current_user.username))
    # form.name.data = current_user.name
    # form.location.data = current_user.location
    # form.about_me.data = current_user.about_me
    return render_template('edit_profile.html',form=form)

疑问：注释的内容一定要添加么？

回答：需要添加。如果 form.validate_on_submit() 验证失败，即用户第一次访问编辑页面，注释的代码可以直接将用户先前的资料数据填入表单。这样渲染的编辑页面可以直接显示先前的用户资料，这样有利于用户可以不用修改每一个用户资料数据，只修改部分数据即可。